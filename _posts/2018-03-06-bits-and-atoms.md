---
layout: post
title:  Bits and Atoms
permalink: bits-and-atoms
date:   2018-03-06 9:45:12
categories: software
comments: true
---
The tools we have available to us today are simply amazing!  I’ve been writing software since I was a kid. Back in the 80s it was a combination of writing software **and** building hardware. Then the hardware sort of disappeared.  The internet came, then the cloud, and the digital bits were all that really mattered.

For 15 years, I have totally forgotten about hardware.  Sure, I build apps that run on iPhones and Android devices; and yes I work on MacPros.  I think about RAM and disk space, cores and graphics cards, but I don't assemble them. They are just products, akin to tools.

And then 4 years ago I bought an [arduino kit](http://arduino.cc). It reminded me of when I was 10 and built my first RC car.  Quickly I was turning lights on and off, making buzz sounds, spinning motors, controlling servos, monitoring temperature, etc.  It’s basic stuff but it was fantastic!  The coolest thing about Arduino's is that you program them!  So it's not only electronics, it's also programming.  And just like that I could write software that interacted with the physical things in my life.  Bits and atoms, software **and** hardware together again, and the ideas started to flow.

## Thing Dev board
Naturally I wanted to do more and more.  I wanted to combine electronic projects with my other work.  I found the [Thing Dev board](https://www.sparkfun.com/products/13231) that is like a simple arduino with a wifi chip onboard.  This got me a step closer.  

After some searching [I found a library ](https://github.com/firebase/firebase-arduino) [that works with Firebase](https://firebase.google.com/) and the Thing dev board.  (I'll dive into firebase at a later time, but in it's simplest form it's realtime database that's in the cloud.)  Firebase has libraries for iOS, Android, Ember, and Node.  All are platforms that I work with almost daily.

With the firebase library, I was now able to glue all my worlds together.  So I built an arduino based project that writes temperature and humidity data to firebase.  

![Thing with a DHT22 temperature and humidity sensor]({{"/img/thing-temp-bot.JPG" | absolute_url}})  

Then I built an ember website that reads that data real-time.  I quickly followed that up with an Android app and then an iOS app, both of which show the data from the Thing dev boards real-time.

I had basically built a poor mans version of a cloud enable thermometer.  The total cost of the software, $0.00.  That's right, free.  The hardware cost me about $30 for each Thing board and peripherals. You can actually get a [really cool IoT kit](https://www.sparkfun.com/products/13799) for about $40.00. I think that's pretty darn cheap, and well worth the money :)

So needless to say I'm really excited about where this technology can go and already have some home automation plans.
