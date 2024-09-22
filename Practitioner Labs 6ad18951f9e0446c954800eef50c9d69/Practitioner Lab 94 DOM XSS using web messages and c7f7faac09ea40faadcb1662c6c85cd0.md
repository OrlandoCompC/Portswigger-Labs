# Practitioner Lab 94: DOM XSS using web messages and a JavaScript URL

---

This lab demonstrates a DOM-based redirection vulnerability that is triggered by web messaging. To solve this lab, construct an HTML page on the exploit server that exploits this vulnerability and calls the `print()` function.

![Untitled](Practitioner%20Lab%2094%20DOM%20XSS%20using%20web%20messages%20and%20c7f7faac09ea40faadcb1662c6c85cd0/Untitled.png)

When a message is received, it extracts the URL from the message data. If the URL starts with either “http:” or “https:”, it redirects the current page to that URL. Otherwise, it does nothing.

Using a link from the website I used it to see how the webpage reacts.

![Untitled](Practitioner%20Lab%2094%20DOM%20XSS%20using%20web%20messages%20and%20c7f7faac09ea40faadcb1662c6c85cd0/Untitled%201.png)

This Redirected me which means that I can just add a javascript link somewhere in the link and maybe I can execute javascript.

```
	<iframe id="target_website"  src="https://0ac500b60475a72e83875a8700a50078.web-security-academy.net/" onload="this.contentWindow.postMessage('javascript:print()//https:','*')"></iframe>
```

The following payload solved it. 

This is because of how it works. The script was only checking if it contained javascript, it didn’t really care if it was on the start or at the end as long as the http was present. 

Because of this I used the http as a comment at the end.