# Practitioner Lab 111: Server-side template injection with information disclosure via user-supplied objects

---

This lab is vulnerable to server-side template injection due to the way an object is being passed into the template. This vulnerability can be exploited to access sensitive data.

To solve the lab, steal and submit the framework's secret key.

You can log in to your own account using the following credentials:

```
content-manager:C0nt3ntM4n4g3r
```

![Untitled](Practitioner%20Lab%20111%20Server-side%20template%20injectio%202d3e18ad2b344df9968cee7e58805cb7/Untitled.png)

Caused a basic error which resulted in me seeing which engine its using.

i saw the django template but after looking deeper and using the {% debug %} I also found jinja 

![Untitled](Practitioner%20Lab%20111%20Server-side%20template%20injectio%202d3e18ad2b344df9968cee7e58805cb7/Untitled%201.png)

The debug gave me all the objects in the template including the settings object.

![Untitled](Practitioner%20Lab%20111%20Server-side%20template%20injectio%202d3e18ad2b344df9968cee7e58805cb7/Untitled%202.png)

![Untitled](Practitioner%20Lab%20111%20Server-side%20template%20injectio%202d3e18ad2b344df9968cee7e58805cb7/Untitled%203.png)

I then started looking at how i could see how I could get the secret key and then I found that I could use 
• `{{settings.SECRET_KEY}}`

This gave me the following and solved the lab.

![Untitled](Practitioner%20Lab%20111%20Server-side%20template%20injectio%202d3e18ad2b344df9968cee7e58805cb7/Untitled%204.png)