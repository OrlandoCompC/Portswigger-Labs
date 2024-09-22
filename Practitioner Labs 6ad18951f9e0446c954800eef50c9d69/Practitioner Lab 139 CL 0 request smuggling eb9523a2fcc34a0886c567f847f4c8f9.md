# Practitioner Lab 139: CL.0 request smuggling

---

This lab is vulnerable to CL.0 request smuggling attacks. The back-end server ignores the `Content-Length` header on requests to some endpoints.

To solve the lab, identify a vulnerable endpoint, smuggle a request to the back-end to access to the admin panel at `/admin`, then delete the user `carlos`.

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled.png)

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%201.png)

I will start by looking for a static file and see if its vulnerable.

I first make it into a http 1.1 request I then add a smuggled request below. 

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%202.png)

Try to send a post request. 

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%203.png)

sending the foo: x to block the next request. 

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%204.png)

This can be seen when I go see the response to the next request. 

IMPORTANT: Must have the 

**Connection: Keep-Alive**

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%205.png)

When you do the /admin It should show you the admin page on the other request.

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%206.png)

Now I just open the page and delete the user. 

![Untitled](Practitioner%20Lab%20139%20CL%200%20request%20smuggling%20eb9523a2fcc34a0886c567f847f4c8f9/Untitled%207.png)

This solved the lab.