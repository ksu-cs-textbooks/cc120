---
title: "URIs and URLs"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---

Before a web request can be made, the browser needs to know where the resource requested can be found.  This is the role that a Universal Resource Locator (a URL) plays.  A URL is a specific kind of Universal Resource Indicator (URI) that specifies how a specific resource can be retrieved. 

{{% notice info %}}
__URLs and URIs__
The terms URL and URI are often used interchangeably in practice.  However, a URL is a specific subset of URIs that indicate _how to retrieve a resource over a network_; while a URI identifies a unique resource, it does not necessarily indicate how to retrieve it.  For example, a book's ISBN can be represented as a URI in the form _urn:isbn:0130224189_.  But this URI cannot be put into a browser's Location to retrieve the associated book.
{{% /notice %}}

A URI consists of several parts, according to the definition (elements in brackets are optional):

`
URI = scheme:[//[userinfo@]host[:port]]path[?query][#fragment]
`

Let's break this down into individual parts:

__scheme:__ The scheme refers to the resource is identified and (potentially) accessed.  For web development, the primary schemes we deal with are _http_ (hyper-text transfer protocol), _https_ (secure hyper-text transfer protocol), and _file_ (indicating a file opened from the local computer).  

__userinfo:__ The userinfo is used to identify a specific user.  It consists of a username optionally followed by a colon (`:`) and password.  We will discuss its use in the section on HTTP authentication, but note that this approach is rarely used today, and carries potential security risks.

__host:__ The host consists of either a fully quantified domain name (i.e. google.com, cs.ksu.edu, or gdc.ksu.edu) or an ip address (i.e. `172.217.1.142` or `[2607:f8b0:4004:803::200e]`).  IPv4 addresses _must_ be separated by periods, and IPv6 addresses must be closed in brackets.  Additionally, web developers will often use the loopback host, `localhost`, which refers to the local machine rather than a location on the network.

__port:__ The port refers to the port number on the host machine.  If it is not specified (which is typical), the default port for the scheme is assumed: port 80 for HTTP, and port 443 for HTTPS.  

__path:__ The path refers to the path to the desired resource on the server.  It consists of segments separated by forward slashes (`/`).  

__query:__ The query consists of optional collection of key-value pairs (expressed as key:value), separated by ampersands (`&`), and proceeded by a question mark (`?`).  The query string is used to supply modifiers to the requested resource (for example, applying a filter or searching for a term).  

__fragment:__ The fragment is an optional string proceeded by a hashtag (`#`).  It identifies a portion of the resource to retrieve.  It is most often used to auto-scroll to a section of an HTML document, and also for navigation in some single-page web applications.


Thus, the URL `https://google.com` indicates we want to use the secure HTTP scheme to access the server at google.com using its port 443.  This should retrieve Google's main page.

Similarly, the url `https://google.com/search?q=HTML` will open a Google search result page for the term HTML (Google uses the key `q` to identify search terms). 