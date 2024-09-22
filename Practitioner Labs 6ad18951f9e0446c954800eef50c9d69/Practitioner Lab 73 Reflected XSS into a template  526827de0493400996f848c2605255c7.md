# Practitioner Lab 73: Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped

---

This lab contains a reflected cross-site scripting vulnerability in the search blog functionality. The reflection occurs inside a template string with angle brackets, single, and double quotes HTML encoded, and backticks escaped. To solve this lab, perform a cross-site scripting attack that calls the alert function inside the template string.

![Untitled](Practitioner%20Lab%2073%20Reflected%20XSS%20into%20a%20template%20%20526827de0493400996f848c2605255c7/Untitled.png)

I saw a ` ` and knew this was a template. I knew I could inject into this using the ${} and used this to inject an alert() into it.