---
layout: post
title:  Bits and Atoms
permalink: bits-and-atoms
date:   2017-02-23 9:45:12
categories: software
comments: true
---
The tools we have available to us today are simply amazing!  I’ve been writing software since I was a kid. Back in the 80s it was a combination of writing software and building hardware. Then the hardware sort of disappeared.  The internet came, then the cloud, and the bits were all that really mattered.

And then, one day, the hardware came back into my world.  I bought an [arduino kit](http://arduino.cc) a couple of years ago and it blew my mind.  I was able to build physical things and program them again.  All the bits I had been pushing around had finally ended right back in my hands and I was turning lights on and off, making buzz sounds, monitoring temperature, etc.  It’s basic stuff, but **I** wired it up and **I** programmed it.  I made it!

I tinkered around and had fun playing with electronics.  I learned to solder, I learned about circuits, it was sort of like science class in my office.  Everything I built was offline.  Like a lamp.  Then [SparkFun](https://sparkfun.com) released their [Thing Dev board](https://www.sparkfun.com/products/13231).  Simply amazing! This $15 board could be programmed like an arduino, but it had wifi built in.  Really incredible! I had a lot of fun with it.

I rebuilt [TallyThings](https://tallythings.com) to use a cloud service called [firebase](https://firebase.google.com/).  I won’t go into the details here about it, but it’s a fantastic service that does some really amazing things.  By leveraging Firebase, I was able to make tallythings real-time.  So you could be on the website and tally up a count, and you would see the changes live on your iPone and/or iPad.  The key is real-time.

So I wanted to hook my thing dev board up to Tallythings.com too.  I thought it would be awesome to have a physical button to tap that would update the tally realtime across all my devices.  That was about 12 months ago, and I hit a roadblock.  The tooling just wasn’t there yet.

About a week ago I was looking at Firebase again and found an SDK that I could use to hook my Thing Dev board up to Firebase.  (software lesson, if it’s not there and you don’t know how to build it, just wait, someone smarter than you will build it)  So I downloaded the example from the SDK and in 10 minutes I was talking to Firebase from a tiny little $15 board. It’s not integrated into tallythings, but it is working well with firebase!

So what did I do then?  Well, I built an ember app that connects to Firebase too.  Then I built an Android app, and an iPhone app too.  From any of these places I could read the temperature data and also turn on a light on the dev board. I could literally tap a screen and a light would turn on in my den. So amazing!

So great, but how much does it cost? The cost for all of the software is $0.00.  That’s right, all of the software is running on google’s cloud platform and I pay nothing for it.  The hardware costs are around $30 for each Humidity/Temperature Hudbot.

And just like that, hadware has become really important to me again.  I have a bazillion ideas that I want to build.  Right now I'm waiting for another piece to get shipped to me, more on that later.  So be on the lookout for more from me on this topic.
