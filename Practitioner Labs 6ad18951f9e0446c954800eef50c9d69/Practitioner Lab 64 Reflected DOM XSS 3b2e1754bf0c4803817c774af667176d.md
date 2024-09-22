# Practitioner Lab 64 : Reflected DOM XSS

---

This lab demonstrates a reflected DOM vulnerability. Reflected DOM vulnerabilities occur when the server-side application processes data from a request and echoes the data in the response. A script on the page then processes the reflected data in an unsafe way, ultimately writing it to a dangerous sink.

To solve this lab, create an injection that calls the `alert()` function.

I started by trying to put a canary value which I could search for and see where it is being reflected. 

![Untitled](Practitioner%20Lab%2064%20Reflected%20DOM%20XSS%203b2e1754bf0c4803817c774af667176d/Untitled.png)

I used 

```
\"-alert(1)}// 
```

how this works is because the “ is being \, but this character can also be \so by putting \\ I am negating the original \ this using the “ to break out of the string, I am then using the } to end the section and the // to comment out anything behind it because in javascript // is a comment. 

\”alert(1)

<h1> the search result is “\\”-alert(1)}//”</h1>