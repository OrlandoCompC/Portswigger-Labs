# Practitioner Lab 66: Reflected XSS into HTML context with most tags and attributes blocked

---

This lab contains a reflected XSS vulnerability in the search functionality but uses a web application firewall (WAF) to protect against common XSS vectors.

To solve the lab, perform a [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) attack that bypasses the WAF and calls the `print()` function.

![Untitled](Practitioner%20Lab%2066%20Reflected%20XSS%20into%20HTML%20contex%20ecb48a245b9543598f2fe705ab248ccf/Untitled.png)

I captured this request and put it inside of the intruder and used a list of html tags to see which one would work.

After this I found that the body tag worked so I used this tag and then tried to see which events worked.

![Untitled](Practitioner%20Lab%2066%20Reflected%20XSS%20into%20HTML%20contex%20ecb48a245b9543598f2fe705ab248ccf/Untitled%201.png)

here is an example of the payload 

From here I decided to use something I could control which is the resize so I sent it to the victim on a iframe and also resized it there. This solved the lab.

![Untitled](Practitioner%20Lab%2066%20Reflected%20XSS%20into%20HTML%20contex%20ecb48a245b9543598f2fe705ab248ccf/Untitled%202.png)