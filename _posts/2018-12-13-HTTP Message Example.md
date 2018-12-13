---
layout:     post
title:      The Hypertext Transfer Protocol (HTTP)
subtitle:   HTTP protocol
date:       2018-12-13
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - Web Technology
---

## Background

The `HTTP protocol` enables web servers and browsers to exchange data over the 
Internet or an intranet. The `World Wide Web Consortium (W3C)`, and international
community that develops standards, is responsible for revising and maintaining
this protocol.

In general an HTTP-based Uniform Resource Locator(URL) has below format:

>protocol://[host.]domain[:port][/context][/resource][?query string path variable]

or

>protocol://IP address[:port][/context][/resource][?query string path variable]
   
 
## HTTP Request

The HTTP request consists of three components:
- Method, Uniform Resource Identifiers(URI), Protocol/Version
- Request headers
- Entity body


`HTTP Request Example:`

    POST /examples/default.jsp HTTP/1.1
    Accept: text/plain; text/html
    Accept-Language: en-gb
    Connection: Keep-Alive
    Host: localhost
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.5; en-US;
    rv:1.9.2.6) Gecko/20100625 Firefox/3.6.6
    Content-Length: 30
    Content-Type: application/x-www-form-urlencoded
    Accept-Encoding: gzip, deflate
    (CRLF)
    lastName=Blank&firstName=Mike

<br/>

> POST /examples/default.jsp HTTP/1.1

The method-URI-protocol version appears as the first line of the request. 
Here the POST is the request method, an HTTP request can use one the many
request methods specified in the HTTP standards. HTTP 1.1 supports seven
request types: `GET`, `POST`, `HEAD`, `OPTIONS`, `PUT`, `DELETE` and `TRACE`. GET and 
POST are the most commonly used in Internet applications.


In an HTTP request, the request header contains useful information about 
the client environment and the entity body for the request. For instance, 
it may contain the language the browser is set for, the length of the 
entity body, and so on. `Each header and entity body is separated by a 
carriage return/linefeed (CRLF) sequence`


Below is the `entity body` for example HTTP request:

> lastName=Blank&firstName=Mike



### HTTP Response

Similar to the HTTP request, the HTTP response also consists of three parts:
- Protocol, Status Code, Description
- Response headers
- Entity body


`HTTP Response Example:`

    HTTP/1.1 200 OK
    Server: Apache-Coyote/1.1
    Date: Thu, 29 Sep 2013 13:13:33 GMT
    Content-Type: text/html
    Last-Modified: Wed, 28 Sep 2013 13:13:12 GMT
    Content-Length: 112
    (CRLF)
    <html>
    <head>
    <title>HTTP Response Example</title>
    </head>
    <body>
    Welcome to Brainy Software
    </body>
    </html>



The first line of the response header is similar to the first line of the request header.
It tells you that the protocol used is HTTP version 1.1 and that the request succeeded. 
Status code `200` is only issued if the web server was able to find the resource requested.
If a resource cannot be found or the request cannot be understood, the server sends a different
status code. For instance `401` is the status code for an unauthorized access and `405` indicates
the http method is not allowed.


The entity body of the response is the HTML content of the response iteself. The headers and the
entity body are separated by a sequence of `CRLFs`.




 

