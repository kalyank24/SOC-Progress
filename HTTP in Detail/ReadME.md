
# HTTP and HTTPS

## HTTP

**HTTP (Hypertext Transfer Protocol)** is a set of rules used for communication between a web server and a web browser (client). It is used to transmit different types of data from a web server, such as HTML pages, images, videos, and other resources.

**HTTPS (Hypertext Transfer Protocol Secure)** is the secure version of HTTP. HTTPS encrypts the data being transmitted between the client and the server, helping prevent others from viewing the data being sent and received.

When we access a website, the browser needs to make requests to a web server for different resources, such as HTML pages, images, and other assets, and then download the responses.

---

# URL (Uniform Resource Locator)

A **URL (Uniform Resource Locator)** is primarily an instruction that specifies how to access a resource on the internet.

Example:

```text
http://user:password@tryhackme.com:80/view-room?id=1#task3
```

The different parts of a URL are:

```text
scheme://user:password@host:port/path?query_string#fragment
```

### Scheme

The scheme specifies which protocol should be used to access the resource, such as:

* HTTP
* HTTPS
* FTP

### User

Some services require authentication. A username and password can be included in the URL to authenticate with the service.

### Host

The host is the **domain name or IP address** of the server you want to access.

### Port

The port specifies which network port you are going to connect to. The default port is usually **80 for HTTP** and **443 for HTTPS**, but services can be hosted on ports ranging from **1 to 65535**.

### Path

The path specifies the location or name of the resource you are trying to access.

### Query String

The query string contains additional information that can be sent to the requested path.

### Fragment

The fragment is a reference to a specific location on the requested page. It is commonly used with pages containing a large amount of content, allowing a specific section of the page to be linked directly.

---

# HTTP Requests

It is possible to send a request to a web server using just one line:

```http
GET / HTTP/1.1
```

However, for a richer interaction, additional information may need to be sent. This information is provided through **HTTP headers**, which contain additional details for the web server.

### Example Request

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com
```

### Request Lines

**Line 1:** The request is using the **GET** method to request the homepage (`/`) and specifies that HTTP version 1.1 is being used.

**Line 2:** This tells the web server that we want to access `tryhackme.com`.

**Line 3:** This tells the web server that we are using Firefox 87.0.

**Line 4:** This tells the web server which webpage referred us to the current page.

**Line 5:** HTTP requests end with a blank line to indicate that the request has finished.

---

# HTTP Responses

After receiving a request, the web server sends an HTTP response.

### Example Response

```http
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:02 GMT
Content-Type: text/html
Content-Length: 98

<html>
    <head>
        <title>TryHackMe</title>
    </head>
    <body>
        ..........
    </body>
</html>
```

### Response Lines

**Line 1:** `HTTP/1.1` specifies the HTTP version being used. `200 OK` is the status code indicating that the request was completed successfully.

**Line 2:** This tells us the web server software and its version.

**Line 3:** This contains the date and time of the response.

**Line 4:** The `Content-Type` header tells the client what type of information is being returned, such as HTML, images, or videos.

**Line 5:** `Content-Length` tells the client the size of the response.

**Blank line:** The blank line separates the HTTP headers from the response body.

**Remaining lines:** These contain the requested information. In this example, it is the homepage HTML content.

---

# HTTP Methods

HTTP methods allow the client to specify the intended action when making an HTTP request.

The most commonly used methods are:

### GET

Used to retrieve information from a web server.

### POST

Used to submit data to a web server, such as updating information or creating a new record.

### PUT

Used to submit data to a web server to update or replace information.

### DELETE

Used to delete information or records from a web server.

---

# HTTP Status Codes

When we make a request to a web server, it returns a response along with an **HTTP status code**.

Status codes are divided into five ranges:

| Range   | Category               |
| ------- | ---------------------- |
| 100–199 | Informational Response |
| 200–299 | Success                |
| 300–399 | Redirection            |
| 400–499 | Client Errors          |
| 500–599 | Server Errors          |

## Common HTTP Status Codes

### 200 OK

The request was completed successfully.

### 201 Created

A resource has been successfully created.

### 301 Moved Permanently

The requested resource has been permanently moved to a new location.

### 302 Found

The requested resource has been temporarily moved to a different location.

### 400 Bad Request

Something was incorrect or missing in the client's request.

### 401 Unauthorized

Authentication is required before the client can access the requested resource.

### 403 Forbidden

The client does not have permission to access the requested resource.

### 404 Not Found

The requested page or resource does not exist.

### 405 Method Not Allowed

The requested resource does not support the HTTP method being used.

For example, a resource may not allow a `GET` request when it expects a `POST` request.

### 500 Internal Server Error

The server encountered an unexpected error while processing the request.

### 503 Service Unavailable

The server is currently unable to handle the request, possibly because it is overloaded or undergoing maintenance.

---

# HTTP Headers

**HTTP headers** are additional pieces of information sent between the client and server during HTTP communication.

Headers provide additional information about the request or response.

## Common Request Headers

Request headers are sent from the client to the server.

### Host

Some web servers host multiple websites. The `Host` header tells the server which website the client wants to access.

### User-Agent

The `User-Agent` header tells the web server which software or browser is being used to access the webpage.

### Content-Length

The `Content-Length` header tells the web server how much data is included in the HTTP request.

### Accept-Encoding

This tells the web server which compression methods the browser supports, allowing the server to compress data before transmitting it.

### Cookie

Cookies contain information that is sent to the server to help maintain information about the client.

---

# Common Response Headers

Response headers are returned from the server to the client.

### Set-Cookie

This header tells the browser to store a cookie, which can then be sent back to the web server with subsequent requests.

### Cache-Control

This specifies how long the browser should store the response in its cache before requesting it again.

### Content-Type

This tells the client what type of data is being returned, such as:

* HTML
* CSS
* JavaScript
* Images

The browser uses the `Content-Type` header to determine how to process the returned data.

### Content-Encoding

This specifies the compression method used to reduce the size of the data before it is transmitted.

---

# Cookies

Cookies are stored by the browser when a web server sends a **`Set-Cookie`** header.

After a cookie is stored, subsequent requests to the same website can include the cookie data and send it back to the server.

HTTP is **stateless**, meaning each request is treated independently. Cookies help websites maintain information about a user's session between requests.

Cookies can be used for many purposes, but they are commonly used for **web application authentication**.

The cookie value usually does not contain the user's password in plain text. Instead, it commonly contains a **session identifier or token** that the server uses to identify the user's session.
