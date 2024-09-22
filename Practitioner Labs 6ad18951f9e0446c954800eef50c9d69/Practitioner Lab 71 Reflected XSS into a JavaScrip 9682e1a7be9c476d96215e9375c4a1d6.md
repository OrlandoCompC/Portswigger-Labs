# Practitioner Lab 71: Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped

---

This lab contains a [reflected cross-site scripting](https://portswigger.net/web-security/cross-site-scripting/reflected) vulnerability in the search query tracking functionality where angle brackets and double are HTML encoded and single quotes are escaped.

To solve this lab, perform a cross-site scripting attack that breaks out of the JavaScript string and calls the `alert` function.

I escaped the ‘ and then had to use an alert because I could not use the <> symbols.

![Untitled](Practitioner%20Lab%2071%20Reflected%20XSS%20into%20a%20JavaScrip%209682e1a7be9c476d96215e9375c4a1d6/Untitled.png)

```
lb155\'+alert(1)//
```