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
    * Request methods: 
        * GET: used for retrieving a web resource.
        * Post: used for creating /posting new data up to the web server. Create data
        * Put: used for updating a resource on the server (for update)
        * Delete: used for deleting a resource on the serve
        * Options: used for getting all methods accepted by server. Some server can rejected. Server need to be handle request method. 
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

    * POST提交数据方式
        * HTTP 协议中规定 POST 提交的数据必须在 body 部分中，但是协议中没有规定数据使用哪种编码方式或者数据格式。实际上，开发者完全可以自己决定消息主体的格式，只要最后发送的 HTTP 请求满足上面的格式就可以。但是，数据发送出去，还要服务端解析成功才有意义。一般服务端语言如 PHP、Python 等，以及它们的 framework，都内置了自动解析常见数据格式的功能。服务端通常是根据请求头（headers）中的 Content-Type 字段来获知请求中的消息主体是用何种方式编码，再对主体进行解析。所以说到 POST 提交数据方案，包含了 Content-Type 和消息主体编码方式两部分。
            * application/x-www-form-urlencoded  -->  这是最常见的 POST 数据提交方式。浏览器的原生 <form> 表单，如果不设置 enctype 属性，那么最终就会以 application/x-www-form-urlencoded 方式提交数据。上个小节当中的例子便是使用了这种提交方式。可以看到 body 当中的内容和 GET 请求是完全相同的。
            * multipart/form-data  -->  这又是一个常见的 POST 数据提交的方式。我们使用表单上传文件时，必须让 <form> 表单的 enctype 等于 multipart/form-data。E.g.: 请求示例：
                POST http://www.example.com HTTP/1.1
                Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrGKCBY7qhFd3TrwA

                ------WebKitFormBoundaryrGKCBY7qhFd3TrwA
                Content-Disposition: form-data; name="text"

                title
                ------WebKitFormBoundaryrGKCBY7qhFd3TrwA
                Content-Disposition: form-data; name="file"; filename="chrome.png"
                Content-Type: image/png

                PNG ... content of chrome.png ...
                ------WebKitFormBoundaryrGKCBY7qhFd3TrwA--
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
        * protocol: The application-level protocol used by the client and server, e.g., HTTP, FTP, and telnet.
        * hostname: The DNS domain name (e.g., www.nowhere123.com) or IP address (e.g., 192.128.1.2) of the server.
        * port: The TCP port number that the server is listening for incoming requests from the clients.
        * path-to-file-name: The name and location of the requested resource, under the server document base directory. Even look at a fragment URL resource. Use to  identify a part of the particular resource. 
        A resource could be an actual file (html, image, video) on the server or data documents like (xml, json).
13. URI: Uniform Resource Identifier
    * URI: URI is more general than URL, which can even locate a fragment within a resource. The URI syntax for HTTP protocol is: 
        _http://host:port/path?request-parameters#nameAnchor_
        * The request parameters, in the form of name=value pairs, are separated from the URL by a '?'. The name=value pairs are separated by a '&'.
        * The # (called nameAnchor) identifies a fragment within the HTML document, defined via the anchor tag <a id="anchorName">...</a> or <a name="anchorName"> ...</a>.
14.	Difference b/w URL & URI: 


15.	Response status code: 
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
    * An HTML document is a file containing Hypertext Markup Language, and its filename most often ends in the .html extension. An HTML document is a text document read in by a Web browser and then rendered on the screen.
    * **Def**: An HTML document is a file containing hypertext markup language. HTML code is based on tags, or hidden keywords, which provide instructions for formatting the document. A tag starts with an angle bracket and the 'less than' sign: '<'. The tag ends with an angle bracket and the 'greater than' sign '>'. Tags tell the processing program, often the web browser, what to do with the text. For example, to make the word 'Hello' bold, you would use the opening bold tag <b> and then the closing bold tag </b>, like this:

    <b>Hello</b>

    HTML is defined by the World Wide Web Consortium, an organization that regulates standards for the Internet. Each version of HTML has a set of definitions. Note that HTML is not a programming language. While we often refer to HTML markup as HTML code, programming languages require the processing of logical statements and math. HTML allows the developer to make text documents look engaging and pleasant. In most cases, programming on an HTML document is done with JavaScript.

2.	XML document:
3.  JSON Data;


#### Browsers
1.	* Popular: Chrome/Firefox/Safari/IE/Opera/Mobile browser versions of above
    * Hypermedia: 
    * Can create link in the data document. 


### HTML

1. What is HTML？
    HTML (stands for Hypertext Markup Language):
    * Fundamental technology used to defin the structure of a webpage.
    * HTML is not a programming language, it is a markup language used to tell your browser how to structure the webpages you visit.
    * HTML consists of a series of elements, which you use to enclose, wrap, or mark up different parts of the content to make it appear or act a certain way. 
    * HTML elements tell the browser how to display the content
    * HTML elements are represented by tags
    * HTML tags label pieces of content such as "heading", "paragraph", "table", and so on
    * Browsers do not display the HTML tags, but use them to render the content of the page

    * 
        * The <!DOCTYPE html> declaration defines this document to be HTML5
            * The <!DOCTYPE> declaration represents the document type, and helps browsers to display web pages correctly.
            * It must only appear once, at the top of the page (before any HTML tags).
            * The <!DOCTYPE> declaration is **not case sensitive**.
        * The <html> element is the root element of an HTML page
        * The <head> element contains meta information about the document
        * The <title> element specifies a title for the document
        * The <body> element contains the visible page content
        * The <h1> element defines a large heading
        * The <p> element defines a paragraph
    
2. Elements:
    *  Elements can be nested: one element can be put inside another element.
        *  Block elements form a visible block on a page — they will appear on a new line from whatever content went before it, and any content that goes after it will also appear on a new line. Block-level elements tend to be structural elements on the page that represent, for example, paragraphs, lists, navigation menus, footers, etc. A block-level element wouldn't be nested inside an inline element, but it might be nested inside another block-level element.
        * Inline elements are those that are contained within block-level elements and surround only small parts of the document’s content, not entire paragraphs and groupings of content. An inline element will not cause a new line to appear in the document; they would normally appear inside a paragraph of text, for example an <a> element (hyperlink) or emphasis elements such as <em> or <strong>.
        * Empty Elements: Some elements consist only of a single tag, which is usually used to insert/embed something in the document at the place it is included
    * HTML Headings
        * HTML headings are defined with the <h1> to <h6> tags.
        * <h1> defines the most important heading. <h6> defines the least important heading.
    * <p> HTML paragraphs
    * <a> HTML links
    * <img> HTML images --- The source file (src), alternative text (alt), width, and height are provided as attributes.
    * <button> HTML buttons
    * HTML List: <ul> (unordered/bullet list) or the <ol> (ordered/numbered list) tag, followed by <li> tags (list items).
    * HTML elements with no content are called empty elements. --- <br> is an empty element without a closing tag (the <br> tag defines a line break). 
    * &nbsp html中空格（space）

3. Attributes:
    * Attributes contain extra information about the element which you don't want to appear in the actual content
    ![](https://github.com/Mirandalllll/Web-Design/raw/master/Attributes.png)
    * An attribute should have:
        1. A space between it and the element name.
        2. The attribute name, followed by an equals sign.
        3. An attribute value, with opening and closing quote marks wrapped around it.
            
            * href: HTML links are defined with the <a> tag. The link address is specified in the href attribute: <a href="https://www.w3schools.com">This is a link</a>
            * src: HTML images are defined with the <img> tag. The filename of the image source is specified in the src attribute:<!-- <img src="img_girl.jpg">-->
            * width & height: HTML images also have width and height attributes, which specifies the width and height of the image: <!--<img src="img_girl.jpg" width="500" height="600"> --> The width and height are specified in pixels by default; so width="500" means 500 pixels wide.
            * alt: The alt attribute specifies an alternative text to be used, if an image cannot be displayed. The value of the alt attribute can be read by screen readers. This way, someone "listening" to the webpage, e.g. a vision impaired person, can "hear" the element. <!--<img src="img_girl.jpg" alt="Girl with a jacket">-->. The alt attribute is also useful if the image cannot be displayed (e.g. if it does not exist): <!--<img src="img_typo.jpg" alt="Girl with a jacket">. -->
            * style: The style attribute is used to specify the styling of an element, like color, font, size etc. <!--<p style="color:red">This is a red paragraph.</p>-->
            * lang: 



### JavaScript DOM
1. Bubbling: When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.
    * Let’s say we have 3 nested elements FORM > DIV > P with a handler on each of them:
    <!--<!doctype html>
        <body>
            <style>
                body * {
                margin: 10px;
                border: 1px solid blue;
                }
            </style>

    <form onclick="alert('form')">FORM
    <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
    </div>
    </form>
    </body>-->
