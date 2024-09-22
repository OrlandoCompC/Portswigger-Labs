# Practitioner Lab 118: Parameter cloaking

---

This lab is vulnerable to [web cache poisoning](https://portswigger.net/web-security/web-cache-poisoning) because it excludes a certain parameter from the cache key. There is also inconsistent parameter parsing between the cache and the back-end. A user regularly visits this site's home page using Chrome.

To solve the lab, use the parameter cloaking technique to poison the cache with a response that executes `alert(1)` in the victim's browser.

![Untitled](Practitioner%20Lab%20118%20Parameter%20cloaking%20637c6f6a0efe4a40aa02a2e289799437/Untitled.png)

The cookie was set to be the last one..

![Untitled](Practitioner%20Lab%20118%20Parameter%20cloaking%20637c6f6a0efe4a40aa02a2e289799437/Untitled%201.png)

Looking at this I found a way to change the function that it was calling and this resulted in calling an alert. After I poisoned the cache this script is being used on the home page meaning that anybody that visits the homepage will get an alert popup.

![Untitled](Practitioner%20Lab%20118%20Parameter%20cloaking%20637c6f6a0efe4a40aa02a2e289799437/Untitled%202.png)

This solved the lab. 

```
GET /js/geolocate.js?callback=setCountryCookie&utm_content=extrastuff;callback=alert(1)// 
```