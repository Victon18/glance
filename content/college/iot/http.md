# Http
- HTTP (HyperText Transport Protocol)
- HTTP - Simple request-response protocol layered on TCP/IP
    1. Establish a TCP/IP connection to www.example.com:80
    2. Send a http GET request along connection
    3. Read from the connection the response from the web server
# http method
- GET - Fetch a URL
-  HEAD - Fetch information about a URL
-  PUT - Store to an URL
-  POST - Send form data to a URL and get a response back
-  DELETE - Delete a URL
GET and POST (forms) are commonly used.
REST APIs used GET, PUT, POST, and
DELETE
# Error
|Code| msg | use|
|-|-|-|
|200 |OK |Success|
|307 |Temporary Redirect |Redirection - Browser retries using Location header|
|404 |Not Found|Famous one|
|503 |Service Unavailable|Something crashed on the server|
|500 |Internal Server|Something is messed up on the server|
|501 Not Implemented|Use if web app sends bogus request
|400 |Bad Request|Use if user isn't logged in
|401 |Unauthorized|Use if even logging in wouldn't help
|403 |Forbidden |Not allow to perform request
|550 |Permission denied| not the right user|

# browser cashing control
- HTTP Response Header: Cache-Control: max-age=<Seconds>
Browser can reuse reply younger than the max-age
- Cache-Control: max-age=120- Age out in two minutes.
Frequently used on fetches of static content like images, templates,
CSS, JavaScript.
 - Good: Reduce app startup latency and server load
 - Bad: Changes might not be picked up right away
