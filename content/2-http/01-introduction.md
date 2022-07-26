At the heart of the world wide web is the Hyper-Text Transfer Protocol (HTTP).  This is a protocol defining how HTTP servers (which host web pages) interact with HTTP clients (which display web pages).   

It starts with a request initiated from the web browser or other client.  This request is sent over the Internet using the TCP protocol to a web server.  Once the web server receives the request, it must decide the appropriate response - ideally sending the requested resource back to the browser to be displayed.  The following diagram displays this typical request-response pattern.

![HTTP's request-response pattern](.guides/img/request-response-pattern.png)

This HTTP request-response pattern is at the core of how all web applications communicate.  Even those that use websockets begin with an HTTP request.

|||definition
The HTTP standard, along with many other web technologies, is maintained by the [World-Wide-Web Consortium](https://www.w3.org/) (abbrivated W3C), stakeholders who create and maintain web standards.  The full description of the Hyper-Text Transfer Protocol can be found here [w3c's protocols page](https://www.w3.org/Protocols/).
|||
