---
title: "AJAX"
pre: "11. "
weight: 110
date: 2018-08-24T10:53:26-05:00
---

Asynchronous JavaScript and XML (AJAX) is a term coined by Jesse James Garrett to describe a technique of using the [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) object to request resources directly from JavaScript.  As the name implies, this was originally used to request XML content, but the technique can be used with any kind of data.

### The XMLHttpRequest

The `XMLHttpRequest` object is modeled after how the `window` object makes web requests.  You can think of it as a state machine that can be in one of several possible states, defined by both a constant and an unsigned short value: 

* **UNSENT** or **0** The client has been created, but no request has been made.  Analogus to a just-opened browser before you type an address in the address bar.
* **OPENED** or **1** The request has been made, but the response has not been recieved.  The browser analogue would be you have just pressed enter after typing the address.
* **HEADERS_RECIEVED** or **2** The first part of the response has been processed.  We'll talk about headers in the next chapter.
* **LOADING** or **3** The content of the response is being downloaded.  In the browser, this would be the stage where the HTML is being recieved and parsed into the DOM.
* **DONE** or **4** The resource is fully loaded.  In the DOM, this would be equivalent to the `'load'` event.

![The XMLHttpRequest ready states]({{<static "images/3.8.1.png">}})

#### XMLHttpRequest Properties 

The XMLHttpRequest object also has a number of properties that are helpful:

* `readyState` - the current state of the property
* `response` - the body of the response, an `ArrayBuffer`, `Blob`, `Document`, or `DOMString` based on the value of the `responseType`
* `responseType` - the mime type of response
* `status` - returns an unsigned short with the HTTP response status (or 0 if the response has not been recieved)
* `statusText` - returns a string containing the response string fro the server, i.e. `"200 OK"`
* `timeout` - the number of milliseconds the request can take before being terminated


#### XMLHttpRequest Events 

The XMLHttpRequest object implements the `EventTarget` interface, just like the `Element` and `Node` of the DOM, so we can attach event listeners with `addEventListener()`.  The specific events we can listen for are:

* `abort` - fired when the request has been aborted (you can abort a request with the [XMLHttpRequest.abort()](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/abort) method)
* `error` - fired when the request encountered an error 
* `load` - fired when the request completes successfully
* `loadend` - fired when the request has completed, either because of success or after an abort or error.
* `loadstart` - fired when the request has started to load data
* `progress` - fired periodically as the request receives data 
* `timeout` - fired when the progress is expired due to taking too long

Several of these events have properties you can assign a function to directly to capture the event:

* `onerror` - corresponds to the `error` event
* `onload` - corresponds to the `load` event
* `onloadend` - corresponds to the `loadend` event
* `onloadstart` - corresponds to the `loadstart` event 
* `onprogress` - corresponds to the `progress` event
* `ontimeout` - corresponds to the `timeout` event

In addition, there is an `onreadystatechange` property which acts like one of these properties and is fired every time the state of the request changes.  In older code, you may see it used instead of the `load` event, i.e.:

```js
xhr.onreadystatechange(function(){
    if(xhr.readyState === 4 && xhr.status === 200) {
        // Request has finished successfully, do logic
    }
});
```

### Using AJAX

Of course the point of learning about the XMLHttpRequest object is to perform AJAX requests.  So let's turn our attention to that task.

#### Creating the XMLHttpRequest

The first step in using AJAX is creating the XMLHttpRequest object. To do so, we simply call its constructor, and assign it to a variable:

```js
var xhr = new XMLHttpRequest();
```

We can create as many of these requests as we want, so if we have multiple requests to make, we'll usually create a new XMLHttpRequest object for each.

#### Attaching the Event Listeners 

Usually, we'll want to attach our event listener(s) before doing anything else with the `XMLHttpRequest` object.  The reason is simple - because the request happens asynchronously, it is entirely possible the request will be finished _before_ we add the event listener to listen for the `load` event.  In that case, our listener will _never_ trigger.

At a minimum, you probably want to listen to `load` events, i.e.:

```js
xhr.addEventListener('load', () => {
    // do something with xhr object
});
```

But it is also a good idea to listen for the `error` event as well:

```js
xhr.addEventListener('error', () => {
    // report the error
});
```

#### Opening the XMLHttpRequest 

Much like when we manually made requests, we first need to open the connection to the server.  We do this with the [XMLHttpRequest.open()](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/open) method:

```js
xhr.open('GET', 'https://imgs.xkcd.com/comics/blogofractal.png');
```

The first argument is the [HTTP request method]({{<ref "/2-http/06-request-methods" >}}) to use, and the second is the [URL]({{<ref "/2-http/02-uris-and-urls">}}) to open.  

There are also three optional parameters that can be used to follow - a boolean determining if the request should be made asynchronously (default `true`) and a user and password for HTTP authentication.  Since AJAX requests are normally made asynchronously, and HTTP authentication has largely been displaced by more secure authentication approaches, these are rarely used.

#### Setting Headers 

After the `XMLHttpRequest` has been opened, but before it is sent, you can use [XMLHttpRequest.setRequestHeader()](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/setRequestHeader) to set any [request headers]({{<ref "/2-http/07-request-headers">}}) you need.  For example, we might set an `Accept` header to `image/png` to indicate we would like image data as our response:

```js
xhr.setRequestHeader('Accept', 'image/png');
```

#### Sending the XMLHttpRequest 
Finally, the [XMLHttpRequest.send()](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/send) method will send the request asynchronously (unless the `async` parameter in `XMLHttpRequest.open()` was set to `false`).  As the response is received (or fails) the appropriate event handlers will be triggered.  To finish our example:

```js
xhr.send();
```
