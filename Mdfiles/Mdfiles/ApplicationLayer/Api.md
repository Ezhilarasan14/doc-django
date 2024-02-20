# Application Layer

## Api

<p>
Hypertext Transfer Protocol (HTTP) is an application-layer protocol for transmitting hypermedia documents, such as HTML. It was designed for communication between web browsers and web servers, but it can also be used for other purposes. HTTP follows a classical client-server model, with a client opening a connection to make a request, then waiting until it receives a response. HTTP is a stateless protocol, meaning that the server does not keep any data (state) between two requests.
</p>


## HTTP Headers:
<p>
HTTP headers are additional pieces of information sent between the client and the server in both request and response messages. They convey information about the request or the response, the server, the client, or the data being sent.

Here's an overview of how tokens are typically included in HTTP headers:

### Authorization Header:

The Authorization header is commonly used to include tokens in HTTP requests. The value of this header is typically in the format Bearer <token>, where <token> is the actual access token.

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

```

</p>

### Common Request Headers:

User-Agent: Describes the user agent (browser or client) making the request.

Host: Specifies the domain name of the server (used in virtual hosting).

Accept: Informs the server about the types of media that the client can process.

Authorization: Contains credentials for authenticating the client with the server.

### Common Response Headers:

User-Agent: Describes the user agent (browser or client) making the request.

Host: Specifies the domain name of the server (used in virtual hosting).

Accept: Informs the server about the types of media that the client can process.

Authorization: Contains credentials for authenticating the client with the server.

## HTTP Request Methods:

HTTP defines several request methods indicating the desired action to be performed on the identified resource.

GET: Retrieve data from the server.
POST: Send data to the server to create a new resource.
PUT: Update a resource on the server.
DELETE: Remove a resource from the server.
OPTIONS: Describes the communication options for the target resource.
HEAD: Same as GET but only retrieves headers, not the actual data.

#### CORS (Cross-Origin Resource Sharing):

CORS is a security feature implemented by web browsers to control access to resources located outside of the origin of the document. It prevents web pages from making requests to a different domain than the one that served the web page.

### CORS Headers:

Origin: Indicates the origin of the cross-origin request.

Access-Control-Allow-Origin: Specifies which origin(s) are allowed to access the resource.
Access-Control-Allow-Methods: Specifies the HTTP methods allowed when accessing the resource.
Access-Control-Allow-Headers: Lists which HTTP headers can be used when making the actual request.

### HTTP Response Status Codes:

HTTP response status codes indicate the outcome of a request. The status code is a three-digit number.

Common Status Codes:

200 OK: The request was successful.

201 Created: The request was successful, and a new resource was created.

204 No Content: The server successfully processed the request but there is no content to send.

400 Bad Request: The server could not understand the request due to invalid syntax.

401 Unauthorized: The request requires user authentication.

403 Forbidden: The server understood the request, but it refuses to authorize it.

404 Not Found: The requested resource could not be found on the server.

500 Internal Server Error: A generic error message returned when an unexpected condition was encountered by the server.

## Handling CORS Errors:

When dealing with CORS errors, make sure that the server includes the necessary CORS headers (Access-Control-Allow-Origin, etc.) in its responses. Additionally, the client-side code (JavaScript) needs to handle CORS errors gracefully.

In some cases, using techniques like JSONP, CORS middleware, or adjusting server configurations may be necessary to resolve CORS issues.

These concepts are fundamental to understanding and working with HTTP, whether you are building a web application, a RESTful API, or interacting with web services.