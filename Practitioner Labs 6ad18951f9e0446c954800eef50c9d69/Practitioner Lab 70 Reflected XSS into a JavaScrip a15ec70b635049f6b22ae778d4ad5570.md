# Practitioner Lab 70: Reflected XSS into a JavaScript string with single quote and backslash-escaped

---

This lab contains a reflected cross-site scripting vulnerability in the search query tracking functionality. The reflection occurs inside a JavaScript string with single quotes and backslashes escaped.

To solve this lab, perform a cross-site scripting attack that breaks out of the JavaScript string and calls the alert function.

I started playing with the quotes and I put a </script> after to see how it would react. The ‘ was backslashed but the <script> tag had exited the main tag. 

This meant that I could still execute quote.

![Untitled](Practitioner%20Lab%2070%20Reflected%20XSS%20into%20a%20JavaScrip%20a15ec70b635049f6b22ae778d4ad5570/Untitled.png)

Here is how it looked. 

and this solved the lab