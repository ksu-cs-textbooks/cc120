---
title: "Server Hardware"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---

The server hardware is really nothing more than a computer - essentially the same as your desktop or laptop. It has a CPU, RAM, hard drives, and a network card, just like your PC - often they are exactly the same hardware as you might find in a PC. But in many cases, they may be designed for sustained repeated and heavy use - basically a more robust (and expensive) version of consumer hardware. They often also are designed to use less power and generate less heat. And they often have far more RAM and hard drives than a consumer PC.

Most server hardware is installed in racks instead of the more familiar PC case. This allows a lot of servers to be installed in a single room (often called a data center) and allows more air to flow around the hardware, keeping it cool. Remember, a computer consumes electricity as it runs and generates heat - if you put a bunch of them together in a data center you are using a _lot_ of electricity and producing a _lot_ of heat. Thus, data centers are designed to supply a lot of electricity, and have extremely powerful air conditioning systems to remove all of that waste heat. Many data centers also have an uninterrupted power supply (UPS) system or even a generator to provide backup power during a power outage.

{{<figure title="A data center with multiple server racks by Alexis Lê-Quôc from New York, United States" src="/images/8.2.1.jpg" alt="A data center with multiple server racks">}}

You may have noticed that data centers like the one pictured above don't have a lot of computer monitors - because if the whole purpose of the computer is to serve responses to HTTP requests, you really don't need to hook it up to a monitor very often. Instead, we typically connect to web server hardware through the network, from a regular laptop or PC.

This isn't to say that you can't run a web server from a normal PC or laptop and make it accessible on the web - you certainly can!  However, to do so, you need one other thing - a static IP address - which we'll discuss next.