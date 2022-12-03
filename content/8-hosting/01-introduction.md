---
title: "Introduction"
pre: "1. "
weight: 10
date: 2018-08-24T10:53:26-05:00
---

Earlier, when we [looked at HTTP in Chapter 2]({{<ref "2-http">}}), we discussed how HTTP connects the client (typically a web browser) to a _server_, a specialized program running on a computer connected to the internet that serves web pages (and other files) in response to a HTTP request. This server is what makes your webpages available on the World Wide Web.

Somewhat confusingly, web developers and IT professionals commonly refer to _both_ the program serving HTTP requests _and_ the hardware it runs on as a _server_. To help avoid this confusion in this chapter, we'll refer to the computer running the server as the _server hardware_ and the software program serving HTTP requests as the _server program_.

In this chapter, we will look at exactly what a server (both hardware and program) is, and how it is made accessible on the web. Then we'll examine some of the most widely used of the server programs: Apache, Nginx, and IIS. We'll also discuss setting up domain names and security certificates - all the steps necessary for hosting your own websites. 

{{% notice info %}}
We will look at setting up these servers to serve _static_ content - the kinds of HTML, CSS, and JavaScript files you've been writing in this class. However, it is important to understand that a web server can also _dynamically create_ files to send as a response - as you see every time you use a search engine or an online store. In these cases, the HTML they send is _created by the server_ in response to the requests made by you, the user. This kind of dynamic web content creation is the subject of the follow-on courses, [CC 515 - Full Stack Web Development](https://textbooks.cs.ksu.edu/cc515) and [CIS 526 - Web Application Development](https://textbooks.cs.ksu.edu/cis526).
{{% /notice %}}