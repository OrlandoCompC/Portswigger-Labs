# Practitioner Lab 116: Web cache poisoning via an unkeyed query string

---

This lab is vulnerable to web cache poisoning because the query string is unkeyed. A user regularly visits this site's home page using Chrome.

To solve the lab, poison the home page with a response that executes `alert(1)` in the victim's browser.

I first sent a query string and then changed it and it still gave me a hit, meaning its ignoring the query string but just to make sure I also used a scan to see if burp would be able to catch it. 

![Untitled](Practitioner%20Lab%20116%20Web%20cache%20poisoning%20via%20an%20un%201e471276e5164fcd90af36079d35050a/Untitled.png)

Burp was able to identify it.

![Untitled](Practitioner%20Lab%20116%20Web%20cache%20poisoning%20via%20an%20un%201e471276e5164fcd90af36079d35050a/Untitled%201.png)

![Untitled](Practitioner%20Lab%20116%20Web%20cache%20poisoning%20via%20an%20un%201e471276e5164fcd90af36079d35050a/Untitled%202.png)

The query string was reflected on the webpage. 

Even if I do change the query it still returns a hit meaning that it was cached and it is ignoring the string

![Untitled](Practitioner%20Lab%20116%20Web%20cache%20poisoning%20via%20an%20un%201e471276e5164fcd90af36079d35050a/Untitled%203.png)

This way it would reflect on the site. 

this solved the lab.