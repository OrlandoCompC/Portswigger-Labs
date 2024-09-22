# Practitioner Lab 120: URL normalization

---

his lab contains an XSS vulnerability that is not directly exploitable due to browser URL-encoding.

To solve the lab, take advantage of the cache's normalization process to exploit this vulnerability. Find the XSS vulnerability and inject a payload that will execute `alert(1)` in the victim's browser. Then, deliver the malicious URL to the victim.

![Untitled](Practitioner%20Lab%20120%20URL%20normalization%206158bcdb6b8b436db23b893169914965/Untitled.png)

Here I found that if it was being reflected in this page. 

I then added the xss payload so that it would open an alert to the visitor. 

```
/hello</p><script>alert(1)</script><!--
```

this payload wouldve also solved it.