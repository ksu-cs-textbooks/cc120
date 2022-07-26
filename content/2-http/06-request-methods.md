---
title: "Request Methods"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---

When a web client like a browser makes a request, it must specify the _request method_, indicating what kind of request this is (sometimes we refer to the method as a __HTTP Verb__).

The two most common are _GET_ and _POST_ requests, as these are typically the only kinds supported by browsers.  Other request methods include PUT, PATCH, and DELETE, which are typically used by other kinds of web clients.  We'll focus on just GET and POST requests here.

#### GET 
A _GET_ request seeks to retrieve a specific resource from the web server - often an HTML document or binary file.  GET requests typically have no body and are simply used to retrieve data.  If the request is successful, the response will typically provide the requested resource in its body.

#### POST
The _POST_ request submits an entity to the resource, i.e. uploading a file or form data.  It typically will have a body, which is the upload or form.  

{{% notice info %}}
You can learn about other HTTP Methods in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods).  HTTP Methods are defined in [W3C's RFC2616](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html).
{{% /notice %}}
