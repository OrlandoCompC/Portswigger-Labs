# Practitioner Lab 114: Web cache poisoning with multiple headers

---

This lab contains a web cache poisoning vulnerability that is only exploitable when you use multiple headers to craft a malicious request. A user visits the home page roughly once a minute. To solve this lab, poison the cache with a response that executes `alert(document.cookie)` in the visitor's browser.

The `X-Forwarded-Scheme` HTTP header is used to indicate the original scheme (HTTP or HTTPS) that a client used to connect to a server. It is typically added by intermediaries such as reverse proxies or load balancers that sit between the client and the server. This information can be used by the server to make decisions about how to process the request, for example, whether to serve a secure or non-secure version of a resource.

I did a paramminer and found the X-Forwarded-Scheme and then I did it again when the X-Forwarded-Scheme was added and it found the X-Forwarded-Host

![Untitled](Practitioner%20Lab%20114%20Web%20cache%20poisoning%20with%20mult%20f84c80a7aad1429ab7d02eec76ceaff6/Untitled.png)

When I add the X-Forwarded-Scheme it rediects to the host. at this point nothing obvious is being reflected but when I add the X-Forwarded-Host I can redirect to any site I want such as the exploit server. 

![Untitled](Practitioner%20Lab%20114%20Web%20cache%20poisoning%20with%20mult%20f84c80a7aad1429ab7d02eec76ceaff6/Untitled%201.png)

When the home page loads it loads this script also. Maybe I can get xss on that script and then when the home page is loaded and loads it pops the alert.

![Untitled](Practitioner%20Lab%20114%20Web%20cache%20poisoning%20with%20mult%20f84c80a7aad1429ab7d02eec76ceaff6/Untitled%202.png)

Since when someone visits the page it gets the js file and that is poisoned then the attack is successful

![Untitled](Practitioner%20Lab%20114%20Web%20cache%20poisoning%20with%20mult%20f84c80a7aad1429ab7d02eec76ceaff6/Untitled%203.png)