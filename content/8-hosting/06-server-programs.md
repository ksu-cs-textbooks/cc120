---
title: "Server Programs"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---

Once you have your static IP address, your domain name, and your firewall configured, you are ready to start responding to HTTP requests. This process is handled by a server program - it accepts incoming HTTP an HTTPS requests by determining and sending a response.  In the simplest form, a web server program simply responds with static files that are saved in a particular location - often a folder named `public_html`, `html`, or `www`. Thus, a request for `http://mysite.com/mypage.html` might serve the file `www/mypage.html`. This is exactly how many web server programs operate.

When webserver programs are used to serve files from a directory like this, there is an open question of what to do when a directory rather than a file is requested, i.e. `https://mysite.com` or `https://mysite.com/pictures`.  Most webserver programs configured to serve files will generate a HTML page listing the contents of the directory.  For example, if your `www` folder contained `mypage.html`, `mypage.css`, and the directory `pictures`, it might generate a page like this:

```html
<!doctype>
<html lang="en">
  <head>
    <title>Index of /</title>
  </head>
  <body>
    <h1>Index of /</h1>
    <ul>
      <li><a href="/pictures">pictures/</a></li>
      <li><a href="/mypage.html">mypage.html</a></li>
      <li><a href="/mypage.css">mypage.css</a></li>
    </ul>
  </body>
</html>
```

As the web grew more popular, many developers wanted to serve a specific webpage when a directory was requested rather than have the web server program generate this kind of index. The widely-adopted solution is that if the directory contains a file named `index.html`, that is served instead of a generated index. Further, most web server programs can be configured to serve a 404 instead of generating an index.

Three of the best-known web server programs used today are Apache, Nginx, and IIS. [Apache](https://httpd.apache.org/) is one of the earliest widely-adopted web servers.  It is free and open-source, and because of this, it was used for the bulk of web hosting during the period of rapid growth after the world-wide-web became available to the general public in the 1990s and into the 2000s. As of December 2022, Apache is used by 32% of the websites on the Internet [^1]. [Nginx](https://www.nginx.com/) was developed as a potential successor to Apache.  Also an open-source server, it focuses on being fast and lightweight. As of December 2022, it is used by 34% of the websites on the internet [^2]. While both Apache and Nginx can be installed on multiple operating systems, but for production web servers they are almost exclusively installed on the Linux Operating System (which is also free and open-source). In contrast, Microsoft's [IIS](https://www.iis.net/) runs exclusively on Windows Server, and has a much more limited market share, used by only 5.8% of all websites on the internet[^3]. Setting up these three webservers to serve content is one of the subjects covered in the [CC 510](https://textbooks.cs.ksu.edu/cis527) and [CIS 527](https://textbooks.cs.ksu.edu/cis527/) courses.


Apache, Nginx, and IIS are only a fraction of the many web server programs that are commercially available. In addition, many web server programs (including Apache, Nginx, and IIS) also allow you to write some form of program scripts to generate web pages in addition to serving files. Or, you can even write your own web server programs in just about any programming language.  This is covered in the [CIS 526](https://textbooks.cs.ksu.edu/cis526/) and [CC 515](https://textbooks.cs.ksu.edu/cis526/) courses.

[^1]: According to data gathered by [w3techs.com](https://w3techs.com/technologies/details/ws-apache)

[^2]: According to data gathered by [w3techs.com](https://w3techs.com/technologies/details/ws-nginx)

[^3]: According to data gathered by [w3techs.com](https://w3techs.com/technologies/details/ws-microsoftiis)
