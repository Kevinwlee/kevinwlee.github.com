---
layout: post
title: Arduino Reed Switch
date: "2018-11-20 20:02:22 -0600"
---

A while back I was working on a garage controller and I wanted to know when the door was open or closed.  I noticed a magnetic reed switch on my window and thought aha! That's how you do it.  So I popped it off my window and prototyped this little circuit.

![Reed Switch Gif]({{"/img/reed-switch.gif"}})

```c++
int ledPin = 13;   // LED connected to digital pin 13
int reedPin = 7;   // Pin connected to the reed switch
int val = 0;       // variable to store the read value


void setup() {
  pinMode(ledPin, OUTPUT);      // sets the LED as output
  pinMode(reedPin, INPUT);        // sets Reed as input
}

void loop() {
  checkDoor();
}

void checkDoor() {
  val = digitalRead(reedPin);     // read the input pin
  digitalWrite(ledPin, val);    // sets the LED to the button's value  
}
```
