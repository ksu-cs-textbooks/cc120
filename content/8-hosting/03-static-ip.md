---
title: "Static IP Addresses"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---

You may remember from our discussion of [URIs and URLs in Chapter 2]({{<ref "2-http/02-uris-and-urls">}}) that a HTTP request must be made against a _host_.  This host is specified either by a fully-qualified domain name, or by an Internet Protocol (IP) address. But what exactly is an IP address?

An IP address is an address of a specific computer on the internet. Without such an address, we would not be able to send HTTP requests or responses to a computer, because we would have no idea where to send it. This is much like a mailing addresses in the real world - you need to know where to send a letter for the post office to deliver it.

Now we get to the interesting part - unlike mailing addresses, there are a limited number of IP addresses because we represent them with a specific number of bits (32 bits for IPV4 addresses, and 128 for the new IPV6 addresses).

![IPv4 address format](/images/8.3.1.png)
![IPv6 address format](/images/8.3.2.png)

Because of this limit, internet providers don't assign every customer a unique IP address. Instead, they use a _pool_ of addresses. When your computer connects to the internet, they draw a currently unused IP address from the pool and assign it to your computer. This is your computer's address until you disconnect.  The next time you connect, you may get a different IP address.  It's kind of like parking in a parking garage - you probably won't get the same space every time.

This makes hosting a website from a consumer internet account very difficult, because every time you get a new IP address, you'd need to update everyone about where to find your web server. Also, many consumer ISP agreements actually forbid you from hosting a website on your account - so read your agreements carefully.

In contrast, when you sign up with an ISP as a web host (often a feature of business plans), your ISP provides one or more IP address that your computer(s) will _always_ be assigned. We call these _static IP addresses_ because they don't change. This means that even if your computer is disconnected from the internet temporarily, when you reconnect, you will still have the same IP address. These accounts also typically provide more _upstream_ data (the data your computer sends out across the internet), which is important as a web server will send far more data upstream than a consumer browsing the internet will.

Thus, if you plan on hosting your own website, you want a static IP address provided by a hosting plan with your ISP.