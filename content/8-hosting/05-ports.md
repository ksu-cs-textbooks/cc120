---
title: "Ports"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---

The term _port_ is another that has multiple meanings in Computer Science and can lead to some confusion.  It can refer to a physical port on the computer that you plug something into, i.e. a USB port or a CAT5e networking port. But it has another meaning for software running on a network (like the internet).

Your computer probably is running multiple programs that communicate across a network or the internet - i.e. you might be browsing the web with Chrome, checking your email with Outlook, and chatting with friends on Discord. Your computer and the network it is connected to need a way to route the messages intended for each of these separate applications to the right program. The solution that we use is that each program is assigned a unique _port number_, which is a 16-bit unsigned integer (thus, it can range from 0 to 65535). 

A good analogy is to think of your computer as an apartment building.  The apartment building itself has a street address that is common to all the apartments.  This corresponds to the IP address.  Then, each individual apartment has an apartment number.  You need to provide both the street address and apartment number to send a letter to someone (a program) living in a particular apartment. 

Each port can only be assigned to one program at a time, and this assignment is handled by the operating system (i.e. Windows or Linux). Certain common programs have a _default_ port that we expect them to be assigned, for example:

* HTTP servers use port 80
* HTTPS servers use port 443
* FTP (file transfer protocol) servers use port 20
* DNS servers use port 53
* SMTP email servers use port 25 
* POP3 email servers use port 110
* IMAP email servers use 
port 143
* IRC chat servers use 194

Because of this, when you enter a url in your browser (i.e. https://ksu.edu), the browser will assume the address it is connecting to is the IP address mapped to ksu.edu with port 443 (as the secure http protocol was specified).  If you want to run your server on a non-standard port, it must be included in the URL, i.e. https://ksu.edu:3000 would connect to the IP address mapped to ksu.edu with port 3000.  This is not recommended for the same reasons we use domain names - port numbers are difficult for many users to understand and remember.

Each port represents an opportunity for the outside world to connect to your computer. With that opportunity comes risk - and the potential for cyber attacks against your computer. To lessen this risk, most operating systems use a firewall - a program that limits which ports are open (allowed to accept incoming messages from the network). By default, nearly all your ports are closed by a firewall, including port 80 and 443. In order to make your web server program accessible, you must open these ports by changing your firewall settings.  The exact details of this process differ depending on what firewall and operating system you are using.   
