# Practitioner Lab 112: Web cache poisoning with an unkeyed header

---

This lab is vulnerable to web cache poisoning because it handles input from an unkeyed header in an unsafe way. An unsuspecting user regularly visits the site's home page. To solve this lab, poison the cache with a response that executes `alert(document.cookie)` in the visitor's browser.

![Untitled](Practitioner%20Lab%20112%20Web%20cache%20poisoning%20with%20an%20u%2019feb247f0404dff82d47108bf4204d1/Untitled.png)

Using paraminer, I was able to find the x-forwarded-host was unlinked.

I looked at where the page was trying to get the javascript file which was 

```
/resources/js/tracking.js
```

I then added this to the file path on the exploit server 

![Untitled](Practitioner%20Lab%20112%20Web%20cache%20poisoning%20with%20an%20u%2019feb247f0404dff82d47108bf4204d1/Untitled%201.png)

This allowed me to get the cookie but I had to send the payload multiple times for it to work.