# Practitioner Lab 135: H2.CL request smuggling

---

This lab is vulnerable to request smuggling because the front-end server downgrades HTTP/2 requests even if they have an ambiguous length.

To solve the lab, perform a request smuggling attack that causes the victim's browser to load and execute a malicious JavaScript file from the exploit server, calling `alert(document.cookie)`. The victim user accesses the home page every 10 seconds.

The first thing I do is make a random request to something that I know is not in the page just to know I am smuggling a reuqest.

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled.png)

Now that I know this is effectively smuggling a request I can go to the next steps.

Its important that the x=1 does not have any /r/n after because this would mess up the request. 

Now since the goal of the lab is to poison a javascript file then I got to look for a redirect. 

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%201.png)

This used to be a /resource/js/analytics.js but after deleting the analytics.js with the / before it makes it into a redirect

Folders when you remove the / from them it tends to cause a redirect. 

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%202.png)

By changing the Host I can see the location path in the redirect also changes. 

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%203.png)

Now I went into the exploit server and changed the path so that when it goes here it gets the xss.

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%204.png)

I send this to the intruder and put null payloads this way I can make sure it gets delivered to the victim in a fast and efficient way.

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%205.png)

In the settings I turn off update content length .

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%206.png)

This way I can make sure that at some point the victim will click it. 

![Untitled](Practitioner%20Lab%20135%20H2%20CL%20request%20smuggling%207d24b18b08c04fea94f28df507dc282e/Untitled%207.png)

After sending it many many many times it finally solved.