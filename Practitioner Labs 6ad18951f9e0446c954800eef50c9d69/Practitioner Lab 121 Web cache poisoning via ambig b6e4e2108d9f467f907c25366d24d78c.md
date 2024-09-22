# Practitioner Lab 121: Web cache poisoning via ambiguous requests

---

This lab is vulnerable to web cache poisoning due to discrepancies in how the cache and the back-end application handle ambiguous requests. An unsuspecting user regularly visits the site's home page.

To solve the lab, poison the cache so the home page executes `alert(document.cookie)` in the victim's browser.

![Untitled](Practitioner%20Lab%20121%20Web%20cache%20poisoning%20via%20ambig%20b6e4e2108d9f467f907c25366d24d78c/Untitled.png)

By sending double host headers I saw my exploit server reflect on the site. this means that the js is gonna be fetched from my website.

This has a malicious exploit which gets the cookie of the user. 

![Untitled](Practitioner%20Lab%20121%20Web%20cache%20poisoning%20via%20ambig%20b6e4e2108d9f467f907c25366d24d78c/Untitled%201.png)

It solved the lab.