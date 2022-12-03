---
title: "Domain Names"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

A domain name is a human-readable name that can be used instead of an IP address when making HTTP requests. While not actually required for hosting a website, a domain name is definitely something you'll want to have. After all, you don't want people to have to memorize an IP address to reach your website. 

Domain names are essentially leased (rented) from a domain registrar - a company that sells domain names. Some better-known registrars are:
* Domain.Com
* NameCheap
* GoDaddy
* Google Domains
* Dreamhost
* HostGator
* Network Solutions

A domain registrar works with the Internet Corporation for Assigned Names and Numbers (ICANN), as they "register" the domain with ICANN which oversees the domain name system (DNS). This includes a network of special web servers that respond to a query for a domain name with the corresponding IP address. 

Once you own a domain name, you must also create _name records_ within the DNS network to allow your domain name to be looked up by web browsers. These records are typically entered on a DNS server operated by your domain registrar, though some large institutions (like Kansas State University) operate their own DNS server. Name records have a standard syntax (they are basically text files), but typically are entered through a web interface that can look different depending on which registrar you are working with.  You can read more about the specific name records in this [article by Cloudflare](https://www.cloudflare.com/learning/dns/dns-records/).

Once you have your computer assigned a static ip address, and a domain name registered that points at that address, the next step is to ensure that the correct ports are open on your server hardware's operating system.

{{% notice warning %}}
As domain name to IP mappings are cached at multiple points along this network, as well as your ISP and web browser, changes to where a domain name point can take up to a day to percolate through this whole system. This delay often surprises new web developers, who are used to the "instant response" of most computing systems.
{{% /notice %}}
