## HTTP ##

HyperText Transfer Protocol- is a protocol that allows fetching of resources such as HTML. 

Foundation of data exchange on the web and paved way for client-server protocol.

Client-Server Protocol: requests initiated by the recipient (e.g. web browser) sent in HTTP to server. Server responds with HTML that browser understands. 

HTTP is common language that client and server can use to communicate. Messages sent by client are requests. Messages sent by server are responses. 

#### Commands: ####

* GET- GET data from server for client (e.g In Twitter- receive twitter feed with all tweets from today)
* POST- send data from client and ADD to server (e.g. In Twitter- create new user and add to Twitter servers.
* PUT- client sends data and UPDATE data that already exists on server (e.g. In Twitter- you made a tweet but want to edit it)
* DELETE- DELETE specified data from server (e.g. In Twitter- Delete a tweet or user account)

Also used for other data such as images, videos, HTML form data. 

AJAX- HTTP can also be used to fetch part of documents to update web pages on demand.

Responses: 

Server sends two main things: 
1. HTTP message:
e.g. status codes 200 messages- Successful, 404 messages Not Found
2. Data such as HTML (can also send other data)

Go to example.com, Open developer console Network tab, unselect everything (e.g. filter and disable cache). 

When refresh page: 

Data that transferred is shown. When click on item- 
Headers tab shows what was requested (e.g. http://example.com). It also shows status code (e.g. 200 OK) and that it was a GET request.
Response- shows HTML that was received from server.

If refresh get a 304 status- not modified status.

#### Sending data ####

2 ways: 

#### Query string ####

Open register form created in html section 

https://robhami.github.io/ZTM_HTML/register.html

Notice form method is: 

```
<form method="GET">
```
When submit form url has details added to end (query strings) denoted by ? it has a key and a value:

```
file:///C:/Users/Rob.000/Documents/coding/zeromasterywebdev/1_HTML/register.html?firstname=&lasttname=&email=&password=&birthday=&cars=volvo

```

In Network developer screen under Headers can see Query string parameters section. Note password is visible (cover this later)

#### Body of request ####

Uses POST method. 

If add password to form then click register, no query string is added to url. In developer screen shows as FORM data (instead of Query String parameters). 
Password is still visible.

#### HTTPS ####
Https is used. S = secure. Communication is jumbled up. Uses a technology called Transport Layer Security (TLS) or its predecessor- Secure Sockets Layer (SSL).





