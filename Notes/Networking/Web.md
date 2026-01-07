Web Applications are split into multiple parts which are apart of two groups. Front end and back end.

Front end consists of everything the user can see. For example the buttons, text inputs, pages, etc. 
HTML, CSS and JS are used for front end development.

Back end is everything you can not see. For example the database, web application firewall, web servers, etc.

# URL
http://user:password@example.com:80/cool-stuff?id=1#task3
This is a URL (it has a bit more than usual URLs). A URL consists of multiple parts.

| Component    | Example       | Description                                                                         |
| ------------ | ------------- | ----------------------------------------------------------------------------------- |
| Scheme       | http or https | Protocol used to access the website                                                 |
| User         | user:password | Some URLs includes a users login details.                                           |
| Host/Domain  | example.com   | Which website you accessing                                                         |
| Port         | 80            | The port number your connecting to. Don't usually see this but its mostly 80 or 443 |
| Path         | cool-stuff    | Specific page or file your accessing                                                |
| Query String | id=1          | Often used for search items or form inputs.                                         |
| Fragment     | task3         | Points to a specific section of a webpage                                           |
# HTTP Messages
HTTP messages are packets of data being exchanged between a user and the web server.
There are two types of HTTP messages:
- HTTP Requests: Sent by the user to trigger actions on the web application
- HTTP Responses: Sent by the server in response the the users request
## HTTP Request
![](/Images/http_request.png)
- Request Line - First part of a HTTP request tells the server what kind of requests it is dealing with. (Method, Path and Version)
- HTTP Methods - Tells the server what action the user wants to perform:
	- Get - Fetch data
	- Post - Send data
	- Put - Updates data
	- Delete - Removes data
	- Patch - Updates part of a resource
	- Head - Fetches headers
	- Options - Tells you what methods are available
	- Trace - Shows which methods are allowed
	- Connect - Create secure connection
- URL Path - Tells the server where to find the resource
- HTTP Version - Shows the protocol version used

Request Headers allow extra information to be sent to the web server about the request. Some common headers are:

| **Request Header** | **Example**                                                                      | **Description**                                                                          |
| ------------------ | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Host               | `Host: tryhackme.com`                                                            | Specifies the name of the web server the request is for.                                 |
| User-Agent         | `User-Agent: Mozilla/5.0`                                                        | Shares information about the web browser the request is coming from.                     |
| Referer            | `Referer: https://www.google.com/`                                               | Indicates the URL from which the request came from.                                      |
| Cookie             | `Cookie: user_type=student; room=introtowebapplication; room_status=in_progress` | Information the web server previously asked the web browser to store is held in cookies. |
| Content-Type       | `Content-Type: application/json`                                                 | Describes what type or format of data is in the request.                                 |
When data is sent to the web server data is located inside the HTTP Request Body.
The formatting of the data can take many forms, but the commons ones being:
- URL Encoded
- Form Data
- JSON
- XML
## HTTP Response
The first line in every HTTP response is called the **Status Line**. Which provides three pieces of information:
- HTTP Version
- Status Code
- Reason Phrase

A Status Code is a number that tells you the outcome of a request. A Reason Phrase explains what happened.
- Informational Responses 100-199
- Successful Response 200-299
- Redirection Messages 300-399
- Client Error Responses 400-499
- Server Error Responses 500-599
Most common being:
- Continue 100
- OK 200
- Moved Permanently 301
- Not Found 404
- Internal Server Error 500

When a web server responds to a HTTP request is includes HTTP response headers. Which provides important information about the response and tell the client how to handle it.

![](/Images/http_response.png)

Some response headers are required such as:
- Date
- Content-Type
- Server
Some common headers are:
- Set-Cookie (For security make sure cookies are set with `HttpOnly` flag so they can't be accessed with JS, and the `Secure` flag so they're only sent over HTTPS)
- Cache-Control
- Location
HTTP response body is where the actual data lives, (HTML, JSON, images, etc).
# Security Headers
HTTP Security Headers help improve the overall security of the web application by providing mitigation against attacks .
(https://securityheaders.io/  can be used to analyse the security headers of any website).
## CSP (Content-Security-Policy)
A CSP headers is an additional security layer that helps mitigate against common attacks.
Example: `Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'`
A CSP header contains:
- default-src - Specifies the default policy of self
- script-src - Where scripts can be loaded from
- style-src - Where CSS style sheets can be loaded from
## HSTS (Strict-Transport-Security)
Ensures the web browsers will always connect over HTTPS.
Example: `Strict-Transport-Security: max-age=63072000; includeSubDomains; preload`
Breakdown:
- max-age - Expiry time in seconds for this setting
- includeSubDomains - Optional setting that instructs the browser to also apply this setting to all subdomains
- preload - Optional setting allows the website to be included in preload lists. Browsers can use preload lists to enforce HSTS before even having their first visit to a website.
## X-Content-Type-Options
Used to instruct browsers not to guess the MIME time of a resource but only use the Content-Type header.
Example: `X-Content-Type-Options: nosniff`
nosniff - Instructs the browser not to sniff or guess the MIME type
## Referrer-Policy
Controls the amount of information send to the destination web server when a user is redirected from the source web server.
Examples:
- `Referrer-Policy: no-referrer`
- `Referrer-Policy: same-origin`
- `Referrer-Policy: strict-origin`
- `Referrer-Policy: strict-origin-when-cross-origin`
Breakdown:
- no-referrer - Completely disables any information being sent about the referrer
- same-origin - Will only send referrer information when the destination is part of the same origin
- strict-origin - Only sends the referrer as the origin when the protocol stays the same
- strict-origin-when-cross-origin - Same as strict-origin except for same-origin requests, where it sends the full URL path in the origin header
