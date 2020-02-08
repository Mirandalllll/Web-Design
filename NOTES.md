# HTML Notes
### 01/08/2020 Wed ###
 
#### Application: Define structure of message.
1.	HTTP: hypertext transfer protocol. (DEF)
2.	State of an application: e.g.: user information. Facebook user login. Once login, state create the application for user. Independently request. Have to bond every single request in all information. 
3.	* HTTP client sends a request message to an HTTP server. The server, in         turn, returns a response message. 
    * HTTP is a pull protocol; the client pulls information from the server.
    * HTTP is a stateless protocol. Negotiate type of response. 
    <!------HTTP 特性------>
    * HTTP 协议构建于 TCP/IP 协议之上，是一个应用层协议，默认端口号是 80
    * HTTP 是无连接无状态的
    ##### HTTP 报文
    * 请求报文：
        * HTTP 协议是以 ASCII 码传输，建立在 TCP/IP 协议之上的应用层规范。规范把 HTTP 请求分为三个部分：状态行、请求头、消息主体。类似于下面这样：
        <method> <request-URL> <version>
        <headers>

        <entity-body>

        * HTTP 定义了与服务器交互的不同方法，最基本的方法有4种，分别是GET，POST，PUT，DELETE。URL全称是资源描述符，我们可以这样认为：一个URL地址，它用于描述一个网络上的资源，而 HTTP 中的 **GET，POST，PUT，DELETE** 就对应着对这个资源的查，增，改，删4个操作。


4.	GET --> HTTP request method (a web). E.G.: GET/index.html HTTP/1.1
    * GET 用于信息获取，而且应该是安全的 和 幂等的。所谓安全的意味着该操作用于获取信息而非修改信息。换句话说，GET 请求一般不应产生副作用。就是说，它仅仅是获取资源信息，就像数据库查询一样，不会修改，增加数据，不会影响资源的状态。幂等的意味着对同一 URL 的多个请求应该返回同样的结果。
        * GET 请求报文示例：
            GET /books/?sex=man&name=Professional HTTP/1.1
            Host: www.example.com
            User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.7.6)
            Gecko/20050225 Firefox/1.0.1
            Connection: Keep-Alive
    
    <!-------POST------->
    * POST 表示可能修改变服务器上的资源的请求。
        * POST / HTTP/1.1
          Host: www.example.com
          User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.7.6)
          Gecko/20050225 Firefox/1.0.1
          Content-Type: application/x-www-form-urlencoded
          Content-Length: 40
          Connection: Keep-Alive

          sex=man&name=Professional  
    * 注意:
        * GET 可提交的数据量受到URL长度的限制，HTTP 协议规范没有对 URL 长度进行限制。这个限制是特定的浏览器及服务器对它的限制
        * 理论上讲，POST 是没有大小限制的，HTTP 协议规范也没有进行大小限制，出于安全考虑，服务器软件在实现时会做一定限制
        * 参考上面的报文示例，可以发现 GET 和 POST 数据内容是一模一样的，只是位置不同，一个在 URL 里，一个在 HTTP 包的包体里
###### Request Headers
5.	HOST: (www.northeastern.edu) domain name - HTTP/1.1 supports virtual hosts.
6.	Accept: image/gif, image/jpeg, */* what type of data I can understand. 
    mime-type-1, mime-type-2, ... - The client can use the Accept header to tell the server the MIME types it can handle and it prefers.
7.	Accept – Language: en-us. Natural language. language-1, language-2, ...      - The client can use the Accept-Language header to tell the server what       languages it can handle or it prefers.
 
8. Accept-Charset: Charset-1, Charset-2, ... - For character set                negotiation, the client can use this header to tell the server which         character sets it can handle or it prefers. Examples of character sets       are ISO-8859-1, ISO-8859-2, ISO-8859-5, BIG5, UCS2, UCS4, UTF8
###### Request Headers
9.	Accept-Encoding: encoding-method-1, encoding-method-2, ... - The client      can use this header to tell the server the type of encoding it supports.
10. Connection: Close|Keep-Alive - The client can use this header to tell        the server whether to close the connection after this request, or to         keep the connection alive for another request.
11.	User-Agent: browser-type - Identify the type of browser used to make the     request. Server can use this information to return different document        depending on the type of browsers.
12. Content-Length: number-of-bytes - Used by POST request, to inform the        server the length of the request body.
13. Content-Type: mime-type - Used by POST request, to inform the server the     media type of the request body.
14. Cookie: cookie-name-1=cookie-value-1, cookie-name-2=cookie-value-2, ...      - The client uses this header to return the cookie(s) back to the server,    which was set by this server earlier for state management.
    
    Connection: Close|Keep-Alive - Specifies whether the connection to the server is open or closed. Content-Length: number-of-bytes - The length in bytes of the body in the response. Content-Type: mime-type - The MIME type of the content. For example, Content-Type: text/html; charset=utf-8
Server: The name of the server that created the response.
Date: The date and time server responded, for example, Wed, 01 Mar 2006 12:00:00 GMT. Set-Cookie: HTTP response header is used to send cookies from the server to the user agent. 


11.	Web resource: is anything that can be obtained from the World Wide Web.
    Some examples are web pages, e-mail, information from databases, images, videos, and web services.
12.	URL: uniform resource locator. used to uniquely identify a resource over     the web. 
    * URL has the following syntax:
    _protocol://hostname:port/path-and-file-name_
    * 4 parts in a URL: 
        * protocol
        * hostname
        * port
        * path-to-file-name. Even look at a fragment URL resource. Use to  identify a part of the particular resource. 
        A resource could be an actual file (html, image, video) on the server or data documents like (xml, json).
13. URI: Uniform Resource Identifier
    * URI: URI is more general than URL, which can even locate a fragment within a resource. The URI syntax for HTTP protocol is: 
        _http://host:port/path?request-parameters#nameAnchor_
        * The request parameters, in the form of name=value pairs, are separated from the URL by a '?'. The name=value pairs are separated by a '&'.
        * The # (called nameAnchor) identifies a fragment within the HTML document, defined via the anchor tag <a id="anchorName">...</a> or <a name="anchorName"> ...</a>.
14.	Difference b/w URL & URI: 

15.	Request methods: 
    * GET: used for retrieving a web resource.
    * Post: used for creating /posting new data up to the web server. Create data
    * Put: used for updating a resource on the server (for update)
    * Delete: used for deleting a resource on the serve
    * Options: used for getting all methods accepted by server. Some server can rejected. Server need to be handle request method. 
16.	Response status code: 
    * The first line of the response message contains the response status code. 
    * Status code is a 3-digit number: 
        * 1xx(informational): request received; server is continuing the process. 
        * 2xx(success): the request was successfully received, understand, accepted and serviced. 
        * 3xx(redirection): further action must be taken in order to complete the request. 
        * 4xx (client error): the request contains bad syntax or cannot be understood. 
        * 5xx (server error): the server failed to fulfill an apparently valid request. 
    * Common status code: 
        * 200 OK: The request is fulfilled.
        * 301：Found & Redirect, but the new location is not temporary.
        * 302：Found & Redirect (or Move Temporarily): Same as 301, but the new location is temporarily in nature. Client should update the references.
        * 400 Bad Request: Server could not interpret or understand the request, probably syntax error in the request message.
        * 401 Authentication Required: The requested resource is protected, and require client’s credential (username/password).
        * 403 Forbidden/Unauthorized: Server refuses to supply the resource, regardless of identity of client. In this case, client is not authorized to access the resource.
        * 404 Not Found: The requested resource cannot be found in the server.
        * 500 Internal Server Error: Caused by an error in the server-side program responding to the request.
        * 501 Method Not Implemented: The request method used is invalid (method name is case sensitive so even misspelling could cause this.)
16.	Request headers：(headers are metadata of your message)
    * Host: domain name – HTTP/1.1 supports virtual hosts.
    * Accept: mime – type-1, mime – type -2, … the client can use the accept header to tell the server the MIME types it can handle and it prefers.
    * Accept encoding: telling the server understand the complex data. (dagaiba huiqucha)
    * Cookie: one of the ways to save, maintaining, state the application.  
    ![](https://github.com/Mirandalllll/Web-Design/raw/master/图片-1.png)
    * Content – Type: value could be any of the MIME types. 


#### Common document type
1.	Html document: 
2.	XML document;
3.  JSON Data


#### Browsers
1.	* Popular: Chrome/Firefox/Safari/IE/Opera/Mobile browser versions of           above
    * Hypermedia: 
    * Can create link in the data document. 


