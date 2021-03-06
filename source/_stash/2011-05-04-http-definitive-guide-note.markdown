---
layout: post
title: "《HTTP: The Definitive Guide》读书笔记"
date: 2011-05-04 19:20
comments: true
categories: notes
---
1.MIME(Multipurpose Internet Mail Extensions):是一个数据格式标签，用来解决不同的电子邮件系统中传输消息时遇到的问题。 
 
MIME是一个文本类型的标签，用一个主要对象类型和一个特指的子类型，中间加上斜杠表示  
例如：

* An HTML-formatted text document would be labeled with type text/html.  
* A plain ASCII text document would be labeled with type text/plain.  
* A JPEG version of an image would be image/jpeg.  

2.URI（Uniform resource identifier）：每个服务器资源都有个名字，这个名字就叫做URI。它是唯一制定的。

3.URL（Uniform resource locator）：是URI的最常用的表示形式。URL表示的是一个资源在特定服务器上的指定位置。它是URI的一个子集。 <!--more-->

URI与URL的区别：

URI例子:  
  ftp://ftp.is.co.za/rfc/rfc1808.txt  
  http://www.ietf.org/rfc/rfc2396.txt  
  ldap://[2001:db8::7]/c=GB?objectClass?one  
  mailto:John.Doe@example.com  
  news:comp.infosystems.www.servers.unix  
  tel:+1-816-555-1212  
  telnet://192.0.2.16:80/  
  urn:oasis:names:specification:docbook:dtd:xml:4.1.2  

URL：指定协议，网络地址和服务器上的资源名。协议多为http。

URN（Uniform Resource Name）：特定内容唯一的名字，与资源目前的位置无关。也是URI的一个子集。

4.http支持几个不同的请求命令，称为http方法。每个http请求消息都有一个方法。这个方法告诉服务器去执行什么动作。

GET：Send named resource from the server to the client.

PUT：Store data from client into a named server resource.

DELETE：Delete the named resource from a server.

POST：Send client data into a server gateway application.

HEAD：Send just the HTTP headers from the response for the named resource.

5.状态码

200：OK. Document returned correctly.

302：Redirect. Go someplace else to get the resource.

404：Not Found. Can't find this resource.

HTTP会和数字状态码一起发送一段解释性的文本，例如：200 OK
        

6.http消息有三部分组成：

1. start line：消息的第一行，表示请求要去做什么或者应答要发生什么。
2. header fields：0个或多个头部信息在start line之后，每个头部信息有一个名字和对应的值组成，用“：”隔开,头部消息用一行空行结束。
3. 在一行空行之后是一个可选的正文消息，不同于上面2种是有组织的并且是文本类型的，这个消息可以是任何类型的数据。

7.TCP/IP

TCP提供：（1）无错的数据传输  （2）有组织的分发  （3）不分段的数据流

8.OSI七层从下到上：物理层，数据链路层，网络层，传输层，会话层，表示层，应用层

9.浏览器访问http页面的步骤：

1. The browser extracts the server's hostname from the URL.
2. The browser converts the server's hostname into the server's IP address.
3. The browser extracts the port number (if any) from the URL.
4. The browser establishes a TCP connection with the web server.
5. The browser sends an HTTP request message to the server.
6. The server sends an HTTP response back to the browser.
7. The connection is closed, and the browser displays the document.

10.Status code classes 

Overall range  Defined range  Category

100-199        100-101        Informational

200-299        200-206        Successful

300-399        300-305        Redirection

400-499        400-415        Client error

500-599        500-505        Server error

11.Header example                    Description

Date: Tue, 3 Oct 1997 02:16:03 GMT  The date the server generated the response

Content-length: 15040               The entity body contains 15,040 bytes of data

Content-type: image/gif             The entity body is a GIF image

Accept: image/gif, image/jpeg, text/html   The client accepts GIF and JPEG images and HTML

Cache-Control: max-age: The max-age value defines the maximum age of the document—the maximum legal elapsed time(in seconds) from when a document is first generated to when it can no longer be                          considered fresh enough to serve.(Cache-Control: max-age=484200)

Expires: Specifies an absolute expiration date. If the expiration date is in the past, the document is no longer fresh.(Expires: Fri, 05 Jul 2002, 05:00:00 GMT)


If-Modified-Since: 

Perform the requested method if the document has been modified since the specified date. This is used in conjunction with the Last-Modified server response header, to fetch content only if the content has been modified from the cached version.

If-None-Match: 

Instead of matching on last-modified date, the server may provide special tags (see ETag) on the document that act like serial numbers. The If-None-Match header performs the requested method if the cached tags differ from the tags in the server's document.

