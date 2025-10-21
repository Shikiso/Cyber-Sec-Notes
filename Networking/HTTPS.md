# Hypertext Transfer Protocol
HTTP is used by the web to display web page data. HTTPS is the secure version of HTTP.
# Requests and Response
When accessing a web page you make a request for its assets. To make this request you need to tell the browser where the resources are.
To do this you use a URL (Uniform Resource Locator).
![[/Images/url.png]]
- Scheme - Instructs what protocol to use
- User - Authentication such as username and password if needed
- Host - The domain name or IP address
- Port - The port you are connecting to (80 HTTP, 443 HTTPS)
- Path - File or location of resource
- Query String - Extra information that can be sent
- Fragment - Reference to a location on the page requested

## Making a Request
You can make a request with online `GET / HTTP/1.1`
![[/Images/get_request.png]]
But you usually send more data for a better experience. ;)

# Methods
HTTP methods are a way for the client to show their intended action when making a request. There are many methods but these are the common ones:
- GET - Used for getting information
- POST - Submitting data
- PUT - Updating information
- DELETE - deleting information

# Status Codes
Status codes are what the server responds with (aside from the webpage resources). These codes are in 5 different ranges:

| **100-199 - Information Response** | These are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request. These codes are no longer very common. |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200-299 - Success**              | This range of status codes is used to tell the client their request was successful.                                                                                                    |
| **300-399 - Redirection**          | These are used to redirect the client's request to another resource. This can be either to a different webpage or a different website altogether.                                      |
| **400-499 - Client Errors**        | Used to inform the client that there was an error with their request.                                                                                                                  |
| **500-599 - Server Errors**        | This is reserved for errors happening on the server-side and usually indicate quite a major problem with the server handling the request.                                              |
## Common Status Codes
| **200 - OK**                     | The request was completed successfully.                                                                                                                                                                                       |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **201 - Created**                | A resource has been created (for example a new user or new blog post).                                                                                                                                                        |
| **301 - Moved Permanently**      | This redirects the client's browser to a new webpage or tells search engines that the page has moved somewhere else and to look there instead.                                                                                |
| **302 - Found**                  | Similar to the above permanent redirect, but as the name suggests, this is only a temporary change and it may change again in the near future.                                                                                |
| **400 - Bad Request**            | This tells the browser that something was either wrong or missing in their request. This could sometimes be used if the web server resource that is being requested expected a certain parameter that the client didn't send. |
| **401 - Not Authorised**         | You are not currently allowed to view this resource until you have authorized with the web application, most commonly with a username and password.                                                                           |
| **403 - Forbidden**              | You do not have permission to view this resource whether you are logged in or not.                                                                                                                                            |
| **405 - Method Not Allowed**     | The resource does not allow this method request, for example, you send a GET request to the resource /create-account when it was expecting a POST request instead.                                                            |
| **404 - Page Not Found**         | The page/resource you requested does not exist.                                                                                                                                                                               |
| **500 - Internal Service Error** | The server has encountered some kind of error with your request that it doesn't know how to handle properly.                                                                                                                  |
| **503 - Service Unavailable**    | This server cannot handle your request as it's either overloaded or down for maintenance.                                                                                                                                     |
# Headers
Headers aren't required but would be a good idea to use them.
## Common Request Headers
﻿These are headers that are sent from the client (usually your browser) to the server. 
- **Host:** Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.  

- **User-Agent:** This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.  

- **Content-Length:** When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.

- **Accept-Encoding:** Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.

- **Cookie:** Data sent to the server to help remember your information (see cookies task for more information).  

## Common Response Headers
These are the headers that are returned to the client from the server after a request.
- **Set-Cookie:** Information to store which gets sent back to the web server on each request (see cookies task for more information).  

- **Cache-Control:** How long to store the content of the response in the browser's cache before it requests it again.  

- **Content-Type:** This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.  

- **Content-Encoding:** What method has been used to compress the data to make it smaller when sending it over the internet.

# Cookies
Cookies are data that is stored on your computing. Cookies are used to remind web servers who you are, for example saving personal settings.
Here is a HTTP request where a cookie is saved:
![[/Images/cookie.png]]
