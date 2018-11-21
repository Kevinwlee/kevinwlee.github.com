---
layout: post
title: Arduino Reed Switch
date: "2018-11-20 20:02:22 -0600"
---

A while back I was working on a garage controller and I wanted to know when the door was open or closed.  I noticed a magnetic reed switch on my window and thought aha! That's how you do it.  So I popped it off my window and prototyped this little circuit.

![Reed Switch Gif]({{"/img/reed-switch.gif"}})

```c++
int ledPin = 13;   // LED connected to digital pin 13
int reed = 0;      // variable to store the reed value

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  checkDoor();
}

void checkDoor() {
  reed = digitalRead(inPin);
  digitalWrite(ledPin, reed);
}
```
