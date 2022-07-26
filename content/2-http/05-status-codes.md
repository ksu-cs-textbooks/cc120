---
title: "Status Codes"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---

A HTTP response includes a status code - a numeric code and a human-readable description. The codes themselves are 3-digit numbers, with the first number indicating a general category the response status falls into.  Essentially, the status code indicates that the request is being fulfilled, or the reason it cannot be.

### 1XX Status Codes

Codes falling in the 100's provide some kind of information, often in response to a `HEAD` or upgrade request. See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a full list.

### 2XX Status Codes

Codes in the 200's indicate success in some form.  These include:

__`200 OK`__ A status of 200 indicates the request was successful.  This is by far the most common response.

__`201 Created`__ Issued in response to a successful POST request, indicates the resource POSTed to the server has been created.

__`202 Accepted`__ Indicates the request was received but not yet acted upon.  This is used for batch-style processes.  An example you may be familiar with is submitting a DARS report request - the DARS server, upon receiving one, adds it to a list of reports to process and then sends a `202` response indicating it was added to the list, and should be available at some future point.

There are additional 200 status codes.  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a full list.

### 3XX Status Codes 

Codes in the 300's indicate redirects.  These should be used in conjunction with a `Location` response header to notify the user-agent where to redirect. The three most common are:

__`301 Moved Permanently`__ Indicates the requested resource is now permanently available at a different URI.  The new URI should be provided in the response, and the user-agent may want to update bookmarks and caches.

__`302 Found`__ Also redirects the user to a different URI, but this redirect should be considered temporary and the original URI used for further requests.

__`304 Not Modified`__ Indicates the requested resource has not changed, and therefore the user-agent can use its cached version. By sending a 304, the server does not need to send a potentially large resource and consume unnecessary bandwidth. 

There are additional 300 status codes.  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a full list.

### 4XX Status Codes 

Codes in the 400's indicate client errors.  These center around badly formatted requests and authentication status.

__`400 Bad Request`__ is a request that is poorly formatted and cannot be understood.

__`401 Unauthorized`__ means the user has not been authenticated, and needs to log in.

__`403 Forbidden`__ means the user does not have permissions to access the requested resource.

__`404 Not Found`__ means the requested resource is not found on the server.

There are _many_ additional 400 status codes.  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a full list.

### 5XX Status Codes 

Status codes in the 500's indicate server errors.  

__`500 Server Error`__ is a generic code for "something went wrong in the server."

__`501 Not Implemented`__ indicates the server does not know how to handle the request method.

__`503 Service Unavailable`__ indicates the server is not able to handle the request at the moment due to being down, overloaded, or some other temporary condition.

There are additional 500 status codes.  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for a full list.