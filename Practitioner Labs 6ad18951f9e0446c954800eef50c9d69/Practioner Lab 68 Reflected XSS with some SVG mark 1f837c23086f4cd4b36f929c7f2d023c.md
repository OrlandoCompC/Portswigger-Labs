# Practioner Lab 68: Reflected XSS with some SVG markup allowed

---

This lab has a simple reflected XSS vulnerability. The site is blocking common tags but misses some SVG tags and events.

To solve the lab, perform a [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) attack that calls the `alert()` function.

```
<svg><animatetransform onbegin=alert(1) attributeName=transform>
```

I used intruder to check which payloads worked, I then found that SVG and animatetransform worked and the onbegin event also worked. 

I then used the cheat to find one.