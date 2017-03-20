---
layout: post
title:  Bits and Atoms
permalink: bits-and-atoms
date:   2017-02-23 9:45:12
categories: software
comments: true
---
The tools we have available to us today are simply amazing!  I’ve been writing software since I was a kid. Back in the 80s it was a combination of writing software **and** building hardware. Then the hardware sort of disappeared.  The internet came, then the cloud, and the bits were all that really mattered.

For 15 years, I have totally forgotten about hardware.  Sure, I build apps that run on iPhones and Android devices; and yes I work on MacPros.  I thought about RAM and disk space, cores and graphics cards, but I didn't build them. They were just products, akin to tools.

And then I bought an [arduino kit](http://arduino.cc). It reminded me of when I was 10 and built my first RC car.  Quickly I was turning lights on and off, making buzz sounds, spinning motors, controlling servos, monitoring temperature, etc.  It’s basic stuff but it was fantastic because I made it!  The coolest thing about Arduino's is that you program them!  So it's not only electronics, it's also programming.  And just like that I could write software that interacted with the physical things in my life.  Bits and atoms, software **and** hardware together again, and the ideas started to flow.

Naturally I wanted to do more and more.  I wanted to combine electronic projects with my other work.  I found the [Thing Dev board](https://www.sparkfun.com/products/13231) which got me a step closer.  Then a few weeks ago [I found a library ](https://github.com/firebase/firebase-arduino) [that works with Firebase](https://firebase.google.com/).  I'll dive into firebase at a later time, but in it's simplest form it's realtime database that's in the cloud.  They have libraries for iOS, Android, Ember, and Node.  All are platforms that I work with almost daily.  I built [tallythings](https://tallythings.com) on firebase.

With the arduino library, I was now able to glue it all my worlds together.  So I built an arduino project that writes temperatue and humidity data to firebase.  Then I built an ember website that reads that data real-time.  I quickly followed that up with an Android app and then an iOS app, both of which show the data from the Thing dev boards real-time.

I had basically built a poor mans version of a cloud enable thermometer.  The total cost of the software, $0.00.  That's write, free.  The hardware cost me about $30 for each Thing board and peripherals. You can actually get a [really cool IoT kit](https://www.sparkfun.com/products/13799) for about $40.00. I think that's pretty darn cheap, and well worth the money :)

So needless to say I'm really excited about where this technology can go.  This is the first of a series of articles and how-to's that I'm writing.  So, if you want to learn more, stay tuned.


--
I tinkered around and had fun playing with electronics.  I learned to solder, I learned about circuits, it was sort of like science class in my office.  Everything I built was offline.  Like a lamp.  Then [SparkFun](https://sparkfun.com) released their [Thing Dev board](https://www.sparkfun.com/products/13231).  Simply amazing! This $15 board could be programmed like an arduino, but it had wifi built in.  Really incredible! I had a lot of fun with it.

I rebuilt [TallyThings](https://tallythings.com) to use a cloud service called [firebase](https://firebase.google.com/).  I won’t go into the details here about it, but it’s a fantastic service that does some really amazing things.  By leveraging Firebase, I was able to make tallythings real-time.  So you could be on the website and tally up a count, and you would see the changes live on your iPone and/or iPad.  The key is real-time.

So I wanted to hook my thing dev board up to Tallythings.com too.  I thought it would be awesome to have a physical button to tap that would update the tally realtime across all my devices.  That was about 12 months ago, and I hit a roadblock.  The tooling just wasn’t there yet.

About a week ago I was looking at Firebase again and found an SDK that I could use to hook my Thing Dev board up to Firebase.  (software lesson, if it’s not there and you don’t know how to build it, just wait, someone smarter than you will build it)  So I downloaded the example from the SDK and in 10 minutes I was talking to Firebase from a tiny little $15 board. It’s not integrated into TallyThings, but it is working well with firebase!

So what did I do then?  Well, I built an ember app that connects to Firebase too.  Then I built an Android app, and an iPhone app too.  From any of these places I could read the temperature data and also turn on a light on the dev board. I could literally tap a screen and a light would turn on in my den. So amazing!

So great, but how much does it cost? The cost for all of the software is $0.00.  That’s right, all of the software is running on google’s cloud platform and I pay nothing for it.  The hardware costs are around $30 for each Humidity/Temperature Hudbot.

And just like that, hadware has become really important to me again.  I have a bazillion ideas that I want to build.  Right now I'm waiting for another piece to get shipped to me, more on that later.  So be on the lookout for more from me on this topic.
