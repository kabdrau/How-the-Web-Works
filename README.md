# How-the-Web-Works

### Part1: Solidify Terminology

What is HTTP?
Hyper Text Transfer Protocol is governs how clients get data from, or send data to, a server.

What is a URL?
Short for Uniform Resource Locator, a URL is an address for some internet resource.

What is DNS?
Short for Domain Name System, this is a system that takes human-readable URLs and converts them into IP addresses.

What is a query string?
The query string allows you to pass key-value pairs into the URL, in the format ?key1=value1&key2=value2...

List two HTTP Verbs and their use cases.
GET - get some data from the server (most pages, search forms)
POST - send some data to the server (pages that change data on server)

What is an HTTP request?
An HTTP request is a request from a client to a server which follows the HTTP protocol (eg a request for HTML from news.google.com)

What is an HTTP response?
An HTTP response is a response from a server to a client which follows the HTTP protocol (eg sending back HTML/CSS/JS/etc)

What is an HTTP header? Give a couple examples of request and response headers you have seen.
Headers provide additional information about the request or the response. Here are some examples:
Request headers: Host, User-Agent, Accept, Cookie, Cache-Control
Response headers: Content-Type, Last-Modified, Set-Cookie, Cache-Control

What happens when you type a URL in a browser?
Your browser “resolves” the name into an IP address using DNS
Your browser makes a request to that IP address, including headers (info about browser, any previous cookies, and other things)
The server sends a response (typically, HTML, with a status code (200 if it was sucessful)
The browser makes a DOM from that HTML, and finds any other resources needed (images, CSS, JavaScript, etc)
The browser makes separate HTTP requests for those resources and receives response from the server for each

### Part2: Practice Tools

Using curl, make a GET request to the icanhazdadjoke.com API to find all jokes involving the word “pirate”
Use dig to find what the IP address is for icanhazdadjoke.com
Make a simple web page and serve it using python3 -m http.server. Visit the page in a browser.

kabdrau@MacBook-Pro How-the-Web-Works % curl https://icanhazdadjoke.com
Don't tell secrets in corn fields. Too many ears around.%   

kabdrau@MacBook-Pro How-the-Web-Works % dig https://icanhazdadjoke.com/

; <<>> DiG 9.10.6 <<>> https://icanhazdadjoke.com/
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 42102
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;https://icanhazdadjoke.com/.	IN	A

;; AUTHORITY SECTION:
.			86376	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2022081300 1800 900 604800 86400

;; Query time: 23 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Aug 13 11:48:51 CDT 2022
;; MSG SIZE  rcvd: 131

kabdrau@MacBook-Pro How-the-Web-Works % python3 -m http.server
Serving HTTP on :: port 8000 (http://[::]:8000/) ...
::1 - - [13/Aug/2022 11:51:49] "GET / HTTP/1.1" 200 -
::1 - - [13/Aug/2022 11:52:08] "GET / HTTP/1.1" 304 -

### Part3: Explore Dev Tools

Build a very simple HTML form that uses the GET method (it can use the same page URL for the action) when the form is submitted.

Add a field or two to the form and, after submitting it, explore in Chrome Developer tools how you can view the request and response headers.

Edit the page to change the form type to POST, refresh in the browser and re-submit. Do you still see the field in the query string? Explore in Chrome how you can view the request and response headers, as well as the form data.

### Part4: Explore the URL API

At times, it’s useful for your JavaScript to look at the URL of the browser window and change how the script works depending on parts of that (particularly the query string).
Try some of the code examples in the Chrome Console so that you can get comfortable with the basic methods and properties for instances of the URL class.