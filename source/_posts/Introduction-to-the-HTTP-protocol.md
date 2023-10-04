---
title: Introduction to the HTTP protocol
date: 2023-10-4 18:14:13
categories:
  - HTTP protocol
tags:
  - HTTP protocol  
---

## Introduction to HTTP Protocol

HTTP (Hypertext Transfer Protocol) is a protocol for transferring hypertext (such as HTML, XML, images, video, etc.) over the Web. It is one of the core protocols of the Web and is used for communication between clients (usually Web browsers) and servers. The following is a brief description of the HTTP protocol:

    Fundamentals:
        HTTP is a request-response based protocol. The client sends an HTTP request and the server receives the request and returns an HTTP response.
        The client is usually a Web browser and the server is a remote computer that stores Web pages and resources.
    
    Communication Method:
        HTTP communication is stateless; each request-response interaction is independent and the server does not maintain any information about the client between requests. This results in the need for each request to contain enough information for the server to understand and process it.
    
    Request Methods:
        HTTP defines different request methods, the most common include:
            GET: Used to get resources.
            POST: Used to submit data, usually for form submissions.
            PUT: Used to update a resource.
            DELETE: Used to delete a resource.
            HEAD: similar to GET, but only fetches the header information of the resource.
        These methods specify the action that the client wants the server to perform.
    
    Status Code:
        HTTP responses include a status code that indicates the result of the request. Common status codes include:
            200 OK: The request was successful.
            404 Not Found: The requested resource does not exist.
            500 Internal Server Error: The server encountered an error.
    
    Headers:
        HTTP requests and responses include headers that contain metadata about the request or response. Headers can include information such as content type, content length, date, etc.
    
    URL:
        URL (Uniform Resource Locator) is used to identify the address of the resource to be accessed. It consists of a protocol, hostname, port, path, and query parameters.
    
    Security:
        HTTP is inherently insecure, as the data transfer is in clear text and is susceptible to eavesdropping and tampering. For added security, HTTPS (HTTP Secure) is often used, which protects the privacy and integrity of communications by encrypting data transmissions.
    
    Versions:
        There are several versions of HTTP, the earliest being HTTP/1.0, with later versions including HTTP/1.1 and HTTP/2. Each version has different features and performance improvements. 1.1 is the more popular version still in use.

HTTP is the foundation in Web applications that allows clients to request and obtain resources on Web servers via URLs, thus enabling the exchange of information and sharing of resources on a global scale. Almost all Web-related operations, from web browsing to API calls, rely on the HTTP protocol.

## URL

A URL (Uniform Resource Locator) is a string used to identify and locate a resource on the Internet.A URL consists of multiple parts that specify the location, protocol, path, and other information about the resource.The structure of a URL is usually as follows:

```
[Protocol]://[Host]:[Port]/[Path]?[Query Parameters]#[Fragment Identifier]

```

    Protocol: The protocol section specifies the protocol or rules used to access the resource, for example:
        http: used to identify the regular HTTP protocol.
        https: Used to identify the secure HTTP protocol where data transfer is encrypted.
        ftp: used for file transfer protocol.
        file: Used for local file system.
    
    host: The hostname or IP address partially specifies the location of the server where the resource resides. Example:
        www.example.com: host name.
        192.168.0.1: IP address.
    
    The Port: Port section is optional and specifies the port number on the server used to access the resource. If not specified, the default port of the protocol is used by default. Example:
        :80: default port for HTTP.
        :443: the default port for HTTPS.
    
    Path: The path section specifies the location of the resource on the server. It can include multiple levels of directories and file names. For example:
        /folder/file.html: specifies the path to the file.
    
    Query Parameters: the Query Parameters section is optional and is used to pass additional parameters to the server, usually in the form of key-value pairs, with & separating multiple parameters. For example:
        ?id=123&name=John: two parameters are passed, id and name.
    
    Fragment Identifier: Fragment Identifier section is optional, used to specify a specific fragment or location in a resource, usually used to locate anchors in a web page. For example:
        #section2: points to a specific part of the document.

In summary, a URL is a way to uniquely identify and locate a resource on the Internet, and its structure consists of multiple parts, each of which provides information about where the resource is located and how it can be accessed. Different protocols and applications can use different URL structures.

## HTTP请求消息

HTTP请求消息是客户端发送给服务器以请求特定资源或执行特定操作的消息。HTTP请求通常由以下几个部分组成：

1. **请求行（Request Line）**：请求行包含请求的方法、目标URL和HTTP协议的版本。通常具有以下格式：

   ```
   [Request Method] [URL] [HTTP version]
   
   ```

   Request Method: indicates the operation to be performed by the server, common methods include:

   ```
   GET: request to get resources.
   POST: request to submit data.
   PUT: request to update the resource.
   DELETE: request to delete the resource.
   ```

   URL: the URL of the target resource of the request.
   HTTP version: the version of HTTP protocol used, such as HTTP/1.1.

2. Request Headers: The request headers contain metadata information related to the request, usually in the form of key-value pairs. The request headers can include:

    ```
    Host: The host name of the specified server.
    User-Agent: client identification information, usually including browser information.
    Accept: Specifies the type of response content that is acceptable.
    Content-Type: used for POST requests, specifies the data type of the request body.
    Authorization: used for authentication credentials and other information.
    ```

    

3. Empty line: request header and request body must be separated by an empty line.

4. Request Body (optional): for some request methods (e.g. POST and PUT), the request body contains the data to be sent to the server, such as form data, JSON data, etc.

The following is a sample HTTP request message:

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/94.0.4606.81 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8

```

In this example, the request line instructs to use the GET method to request the /index.html resource with HTTP version 1.1. The request header contains information such as Host, User-Agent, and Accept.

Note that the content of a specific HTTP request message will vary depending on the application and its needs; for example, a POST request will include the request body, while a GET request usually does not include the request body. The server uses this information to understand the client's request and responds accordingly.

## GET and POST

GET and POST are the two most commonly used request methods in the HTTP protocol, and they differ significantly in the following ways:

    Data transfer method:
        GET: Transmits data via URL parameters.GET requests append the parameters at the end of the URL in the form of key-value pairs, so the data is visible in the URL.
        POST: Transmits data through the request body. a POST request includes the data in the request body, which is not visible in the URL, and is therefore more suitable for transmitting sensitive data.
    
    The data is limited in length:
        GET: Since the data is appended to the URL, there is a limit to the data length and is not suitable for transferring large amounts of data. Browsers and servers have URL length limitations, usually around a few thousand characters.
        POST: There is usually no strict limit on the length of the data in the request body, and it is more suitable for transmitting large amounts of data.
    
    Security:
        GET: Because the data is visible in the URL, it is not suitable for transferring sensitive data such as passwords. Additionally, GET requests are susceptible to caching, bookmarking, and browser history saving, which may lead to data leakage.
        POST: Since the data is in the request body, it is more suitable for transmitting sensitive data as the data is not displayed in the URL.POST requests are also not susceptible to caching and saving.
    
    Idempotency:
        GET: GET requests are usually idempotent. executing the same GET request multiple times does not affect the server because it just fetches the data without changing the server state.
        POST: POST requests are usually not idempotent, and executing the same POST request multiple times may have a different impact on the server, as it is usually used to submit data or change the server state.
    
    Cache:
        GET: GET requests can be cached by the browser, which helps with performance, but can also lead to security issues as sensitive data may be cached locally.
        POST: POST requests are not cached by the browser as it usually changes the server state and is not suitable for caching.
    
    Bookmarks and browser history:
        GET: Since the parameters of a GET request are visible in the URL, they can be easily saved as bookmarks or looked up in the browser history.
        POST: The data from a POST request is not displayed in the URL and is not suitable for saving as a bookmark or looking up in the browser history.

Based on these differences, the choice of using GET or POST requests should usually be made based on specific needs and security requirements.GET is used for operations that fetch data, while POST is used for submitting data and performing operations that change the status of the server.

## HTTP response messages

An HTTP response message is a message sent by the server to the client in response to its request.An HTTP response message usually consists of the following parts:

1. **Status Line**: The status line contains the HTTP protocol version, status code and status phrase of the response. The usual format is as follows:

```
HTTP/1.1 200 OK

```

- HTTP/1.1: version of the HTTP protocol.
- 200: status code, indicating that the request was successful.
- OK: status phrase, a brief description of the status code.

2. Response Headers: The response headers contain metadata information related to the response, usually in the form of key-value pairs. The response headers can include:

- Content-Type: indicates the type of the response content (e.g., text/html, application/json).
- Content-Length: indicates the length of the response content.
- Server: indicates the server information, such as server name and version.
- Date: indicates the date and time when the response was generated.
- Set-Cookie: used to set and manage client-side cookies.

3. Empty line: There must be an empty line after the status line and response header to separate the header and response body.
4. Response body (Response Body): the response body contains the actual response content, such as HTML documents, JSON data, images, etc., the specific content specified by the Content-Type header.

The following is a sample HTTP response message:

```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 1234
Server: Apache/2.4.41 (Unix)
Date: Wed, 04 Oct 2023 12:34:56 GMT

<!DOCTYPE html>
<html>
<head>
    <title>TEXT</title>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>

```

In this example, the status line indicates that the request was successful (status code 200 OK), the response header contains information such as Content-Type, Content-Length, Server and Date, and the response body contains the content of the HTML page.

The status code and status phrase of the HTTP response message indicate the result of the request. Different status codes indicate different situations, such as 200 for success, 404 for resource not found, 500 for internal server error, etc. The client usually processes the response based on the status code. The client usually processes the response based on the status code to decide what to do next.