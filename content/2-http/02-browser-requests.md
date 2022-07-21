Before we get too deep in the details of what a request is, and how it works, let's explore the primary kind of request you're already used to making - requests originating from a browser.  Every time you use a browser to browse the Internet, you are creating a series of HTTP (or HTTPS) requests that travel across the networks between you and a web server, which responds to your requests.

To help illustrate how these requests are made, we have set up a simple static webserver that runs on this Codio box, and serves files from the _public_ directory (seen in the Filetree).  Click on the _Terminal_ window to give it focus, and you should see the Box URL displayed there. Open this url by clicking on it, or copying it to a browser.  Alternatively, you can choose the `Box URL` option from the `Run` menu at the top of the Codio window.

When you open the website with a browser, you should see a page with __Index of Public__ at the top and a list of files in the _public_ directory.  In the Terminal a message: `Recieved Request for /`. 

Now try following the link for _example.html_.  The page should load, and the terminal should have the messages:

```
Recieved Request for /example.html
Serving Request for /example.html
```

Let's add a picture to _example.html_, just below the "hello bird!" line:

```html
<img src="carrierpigeon.png" alt="pigeon">
```

Then refresh the page.  Provided the `src` attribute matches, you should see the image on the page.  And in the terminal:

```
Recieved Request for /example.hml 
Serving /example.html
Recieved Request for /carrierpigeon.png
Serving /carrierpigeon.png
```

The important takeaway here is that the image is requested _separately_ from the HTML file.  As the browser reads the page and encounters the `<img>` tag, it makes an additional request for the resource supplied in its `src` attribute.  When that second request finishes, the downloaded image is added to the web page.

Let's add a CSS file, _example.css_ to the public directory, with content:

```css
body {
  font-weight: bold;
  color: #512888;
}
```

And link it to our HTML document with a `<link>` element in the `<head>`:

```html
<link href="example.css" rel="stylesheet" type="text/css">
```

Now when you refresh the browser, the "Hello Bird! should be K-State purple.  And our terminal should report one more request, this time for _example.css_:

```
Recieved Request for /example.hml 
Serving /example.html
Recieved Request for /carrierpigeon.png
Serving /carrierpigeon.png
Recieved /example.css 
Serving /example.css
```

You can also view the requests being made on the browser side.  Open the Developer Tools and navigate to the Network tab (On Chrome, `View > Developer > Developer Tools`; On Firefox `Tools > Web Developer > Toggle Tools`). Refresh the page, and you'll see each of the files requested, along with useful details like how long it took to download them.