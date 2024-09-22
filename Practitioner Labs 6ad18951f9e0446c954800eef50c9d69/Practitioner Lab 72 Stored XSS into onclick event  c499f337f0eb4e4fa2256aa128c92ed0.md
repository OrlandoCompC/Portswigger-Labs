# Practitioner Lab 72: Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped

---

This lab contains a [stored cross-site scripting](https://portswigger.net/web-security/cross-site-scripting/stored) vulnerability in the comment functionality.

To solve this lab, submit a comment that calls the `alert` function when the comment author name is clicked.

I looked at how to add the xss at the end of the url. What came to mind was the # which allows me to add anything at the end of a valid URL and such I added the xss at the end.

![Untitled](Practitioner%20Lab%2072%20Stored%20XSS%20into%20onclick%20event%20%20c499f337f0eb4e4fa2256aa128c92ed0/Untitled.png)

This solved the lab

```
[https://0a33005004f38a52805767c300f50000.web-security-academy.net/#](https://0a33005004f38a52805767c300f50000.web-security-academy.net/#'-alert(document.domain)-')&apos;-alert(1)-&apos;
```

Another way to solve it couldve been to just put the website and to put a ? at the end and then add the xss string there/ 

```
http://foo?&apos;-alert(1)-&apos;
```

The apos works because at the time that the server is going checking for any ‘ to escape it was an apos but it is then decoded from html which results in the ‘

This works because we are in an html context not javascript, if this was javascript and we inject html encoded things into it , it wouldn’t work

the browser decoded the html values not the server, the server itself doesn’t know how to decode these values.

This is why when we view page source it would show the html encoding still but if you inspect an element it would be decoded. 

I found that I could use HTML encoding not because I read the lab description but because I saw it was inside of HTML context and it would likely work