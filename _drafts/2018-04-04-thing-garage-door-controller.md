---
layout: post
title:  Garage Controller
date:   2018-04-04 18:51
categories: programming
comments: true
---

I knew I couldn’t resist.  Yesterday I wired up a thing dev board to my garage door opener.  It’s a surprisingly simple thing to do.  Now I have an http endpoint that I can hit to open and close my garage.  :)

//Insert video here:

But just hitting a URL isn’t fun right?  Nope, so I’ve hooked it up to a little node service that monitors firebase.  Now all I need to do to open/close my garage is hit change a value in firebase and boom, the door moves.

//Show the app here:


Here’s the Javascript:
```
var admin = require("firebase-admin");
var http = require("http");

admin.initializeApp({
  credential: admin.credential.cert("YOUR-FIREBASE-adminsdk.json"),
  databaseURL: "https://YOUR-FIREBASE-APP.firebaseio.com"
});

// setup firebase ref
var db = admin.database();
var blueRef = db.ref("bots/HB001/blueGarage");
var first = true

blueRef.on("value", function(snapshot) {
  console.log(snapshot.val())

  if (first) {
    first = false;
    return;
  }

  http.request({host:"192.168.0.103", path:"/door/1", port:"80", method: "GET"}, () => {
    console.log("pinging garage");
  }).end();

}, function (errorObject) {
  console.log("The read failed: " + errorObject.code);
});

```

Here’s the arduino code:
```
#include <ESP8266WiFi.h>
#include <ESP8266mDNS.h>

//////////////////////
// WiFi Definitions //
//////////////////////
const char WiFiSSID[] = “YOUR-WIFI-SSID”;
const char WiFiPSK[] = “YOUR-PASSWORD“;

/////////////////////
// Pin Definitions //
/////////////////////
const int LED_PIN = 5; // Thing's onboard, green LED
const int DIGITAL_PIN = 12; // Digital pin to be read

WiFiServer server(80);

void setup()
{
  initHardware();
  connectWiFi();
  server.begin();
  setupMDNS();
}

void loop()
{
  // Check if a client has connected
  WiFiClient client = server.available();
  if (!client) {
    return;
  }

  // Read the first line of the request
  String req = client.readStringUntil('\r');
  Serial.println(req);
  client.flush();

  // Match the request
  int val = -1;              
  if (req.indexOf("/door/1") != -1)
    val = 1; //on

  if (val >= 0) {
    digitalWrite(DIGITAL_PIN, 1);
    delay(500);
    digitalWrite(DIGITAL_PIN, 0);
  }

  client.flush();

  // Prepare the response. Start with the common header:
  String s = "HTTP/1.1 200 OK\r\n";
  s += "Content-Type: text/html\r\n\r\n";
  s += "<!DOCTYPE HTML>\r\n<html>\r\n";
  // If we're setting the LED, print out a message saying we did
  if (val >= 0)
  {
    s += "Garage is now moving";
  }
  else
  {
    s += "Invalid Request.<br> Try /garage/1.";
  }
  s += "</html>\n";

  // Send the response to the client
  client.print(s);
  delay(1);
  Serial.println("Client disonnected");
  val = 0;
}

void connectWiFi()
{
  byte ledStatus = LOW;
  Serial.println();
  Serial.println("Connecting to: " + String(WiFiSSID));
  // Set WiFi mode to station (as opposed to AP or AP_STA)
  WiFi.mode(WIFI_STA);

  // WiFI.begin([ssid], [passkey]) initiates a WiFI connection
  // to the stated [ssid], using the [passkey] as a WPA, WPA2,
  // or WEP passphrase.
  WiFi.begin(WiFiSSID, WiFiPSK);

  // Use the WiFi.status() function to check if the ESP8266
  // is connected to a WiFi network.
  while (WiFi.status() != WL_CONNECTED)
  {
    // Blink the LED
    digitalWrite(LED_PIN, ledStatus); // Write LED high/low
    ledStatus = (ledStatus == HIGH) ? LOW : HIGH;

    // Delays allow the ESP8266 to perform critical tasks
    // defined outside of the sketch. These tasks include
    // setting up, and maintaining, a WiFi connection.
    delay(100);
    // Potentially infinite loops are generally dangerous.
    // Add delays -- allowing the processor to perform other
    // tasks -- wherever possible.
  }
  Serial.println("WiFi connected");  
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
  digitalWrite(LED_PIN, HIGH); // turn off blue led
}

void setupMDNS()
{
  // Call MDNS.begin(<domain>) to set up mDNS to point to
  // "<domain>.local"
  if (!MDNS.begin("garage"))
  {
    Serial.println("Error setting up MDNS responder!");
    while(1) {
      delay(1000);
    }
  }
  Serial.println("mDNS responder started");

}

void initHardware()
{
  Serial.begin(9600);
  pinMode(DIGITAL_PIN, OUTPUT);
  pinMode(DIGITAL_PIN, HIGH);
  pinMode(LED_PIN, OUTPUT);
  digitalWrite(LED_PIN, LOW); //turn on the blue light
}

```
