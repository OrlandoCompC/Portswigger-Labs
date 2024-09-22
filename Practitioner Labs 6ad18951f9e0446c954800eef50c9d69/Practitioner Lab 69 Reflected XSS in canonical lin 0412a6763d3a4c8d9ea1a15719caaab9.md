# Practitioner Lab 69: Reflected XSS in canonical link tag

---

This lab reflects user input in a canonical link tag and escapes angle brackets.

To solve the lab, perform a [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) attack on the home page that injects an attribute that calls the `alert` function.

To assist with your exploit, you can assume that the simulated user will press the following key combinations:

- `ALT+SHIFT+X`
- `CTRL+ALT+X`
- `Alt+X`

Please note that the intended solution to this lab is only possible in Chrome.

This lab was weird, I could see nothing was being reflected so I searched for link and found that the link was part of a rel. 

I injected this into it 

![Untitled](Practitioner%20Lab%2069%20Reflected%20XSS%20in%20canonical%20lin%200412a6763d3a4c8d9ea1a15719caaab9/Untitled.png)

I injected into the URL and it was being reflected

because of this I knew I had to exploit the url

```
https://YOUR-LAB-ID.web-security-academy.net/?%27accesskey=%27x%27onclick=%27alert(1)
```