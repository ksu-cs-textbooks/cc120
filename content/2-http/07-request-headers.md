---
title: "Request Headers"
pre: "7. "
weight: 70
date: 2018-08-24T10:53:26-05:00
---

Request headers take the form of key-value pairs, and represent specific aspects of the request.  For example:

```
Accept-Encoding: gzip
``` 

Indicates that the browser knows how to accepted content compressed in the [Gzip format](https://en.wikipedia.org/wiki/Gzip).

Note that request headers are a subset of _message headers_ that apply specifically to requests.  There are also message headers that apply only to HTTP responses, and some that apply to both.

As HTTP is intended as an extensible protocol, there are a _lot_ of potential headers.  IANA maintains the [offical list of message headers](https://www.iana.org/assignments/message-headers/message-headers.xhtml) as well as [a list of proposed message headers](https://www.iana.org/assignments/message-headers/message-headers.xhtml).  You can also find a categorized list in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)

While there are many possible request headers, some of the more commonly used are:

__Accept__ Specifies the types a server can send back, its value is a MIME type.

__Accept-Charset__ Specifies the character set a browser understands.

__Accept-Encoding__ Informs the server about encoding algorithms the client can process (most typically compression types)

__Accept-Language__ Hints to the server what language content should be sent in.

__Authorization__ Supplies credentials to authenticate the user to the server.  Will be covered in the authentication chapter.

__Content-Length__ The length of the request body sent, in octets 

__Content-Type__ The MIME type of the request body 

__Content-Encoding__ The encoding method of the request body

__Cookie__ Sends a site cookie - see the section on cookies later

__User-Agent__ A string identifying the agent making the request (typically a browser name and version)
