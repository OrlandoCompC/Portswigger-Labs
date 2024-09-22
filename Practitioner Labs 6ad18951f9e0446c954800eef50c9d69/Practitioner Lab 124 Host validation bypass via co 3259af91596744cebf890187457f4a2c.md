# Practitioner Lab 124: Host validation bypass via connection state attack

---

This lab is vulnerable to routing-based [SSRF](https://portswigger.net/web-security/ssrf) via the Host header. Although the front-end server may initially appear to perform robust validation of the Host header, it makes assumptions about all requests on a connection based on the first request it receives.

To solve the lab, exploit this behavior to access an internal admin panel located at `192.168.0.1/admin`, then delete the user `carlos`.

I began the lab by going into my collaborator and sending a request to it./

![Untitled](Practitioner%20Lab%20124%20Host%20validation%20bypass%20via%20co%203259af91596744cebf890187457f4a2c/Untitled.png)

this worked now I will try to send a request to the internal server which most likely will fail

I have the exact admin panel ip so no need to bruteforce.

![Untitled](Practitioner%20Lab%20124%20Host%20validation%20bypass%20via%20co%203259af91596744cebf890187457f4a2c/Untitled%201.png)

![Untitled](Practitioner%20Lab%20124%20Host%20validation%20bypass%20via%20co%203259af91596744cebf890187457f4a2c/Untitled%202.png)

Sending both packets in a single connection resulted in me gaining access to the admin panel

I then opened in browser, intecepted the request and resend it in a single connection with a request to the home page. 

![Untitled](Practitioner%20Lab%20124%20Host%20validation%20bypass%20via%20co%203259af91596744cebf890187457f4a2c/Untitled%203.png)

This solved the lab.

MAKE SURE THE CONNECTION SAYS, keep-alive

```
Connection: keep-alive
```

if it doesn’t you can always change it to it this way you can send multiple packets in a connection.