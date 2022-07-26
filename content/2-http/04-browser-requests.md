---
title: "Browser Requests"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

Now that you are familiar with the network panel, let's explore the primary kind of request you're already used to making - requests originating from a browser.  Every time you use a browser to browse the Internet, you are creating a series of HTTP (or HTTPS) requests that travel across the networks between you and a web server, which responds to your requests.

When you type in an address in your browser (or click a hyperlink), this initiates a HTTP request against the server located at that address. Ideally, the request succeeds, and you are sent the webpage you requested. As the browser parses that webpage, it may also request additional resources linked in that page (such as images, CSS files, and JavaScript files). 

To help illustrate how these requests are made, we'll once again turn to our developer tools.  Open the example page <a href='/examples/2.5.1/index.html' target='_blank'>this link</a>.  On that tab, open your developer tools with `CTRL + SHIFT + i` or by right-clicking the page and selecting "Inspect" from the context menu.  Then choose the "Network" tab:

![Selecting the network tab in the developer tools](/images/2.4.1.png)

The network tab displays details about each request the browser makes.  Initially it will probably be empty, as it does not log requests while not open.  Try refreshing the page - you should see it populate with information:

![The populated network tab](/images/2.4.2.png)

The first entry is the page itself - the HTML file.  But then you should see entries for _site.css_, _brazil.gif_, *fiber-4814456_960_720.jpg*, _jquery-3.5.1.slim.min.js_, and _site.js_.  Each of these entries represents an additional resource the browser fetched from the web in order to display the page.

Take, for example, the two images _brazil.gif_ and *fiber-4814456_960_720.jpg*.  These correspond to `<img>` tags in the HTML file:

```html
<img alt="Paper scene from the film Brazil" src="brazil.gif"/>
<img alt="Fiber optic cables" src="https://cdn.pixabay.com/photo/2020/02/03/00/12/fiber-4814456_960_720.jpg"/>
        
```

The important takeaway here is that the image is requested _separately_ from the HTML file.  As the browser reads the page and encounters the `<img>` tag, it makes an additional request for the resource supplied in its `src` attribute.  When that second request finishes, the downloaded image is added to the web page.

Notice too that while one image was on our webserver, the other is retrieved from [Pixabay.com](https://pixabay.com)'s server.  

You can use the network tab to help debug issues with resources.  Click on one of the requested resources, and it will open up details about the request:

![Request details in the Network Tab](/images/2.4.3.png)

Notice that it reports the status code along with details about the request and response, and provides a preview of the requested resource.