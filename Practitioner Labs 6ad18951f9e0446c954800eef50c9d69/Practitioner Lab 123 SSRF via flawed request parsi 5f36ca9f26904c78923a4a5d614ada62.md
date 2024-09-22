# Practitioner Lab 123: SSRF via flawed request parsing

---

This lab is vulnerable to routing-based SSRF due to its flawed parsing of the request's intended host. You can exploit this to access an insecure intranet admin panel located at an internal IP address.

To solve the lab, access the internal admin panel located in the `192.168.0.0/24` range, then delete the user `carlos`.

![Untitled](Practitioner%20Lab%20123%20SSRF%20via%20flawed%20request%20parsi%205f36ca9f26904c78923a4a5d614ada62/Untitled.png)

First thing I tried was to use the collaborator to see if I could change the host header this way I could see if I had access.

The idea now will be to try multiple host headers or to try to override it . 

![Untitled](Practitioner%20Lab%20123%20SSRF%20via%20flawed%20request%20parsi%205f36ca9f26904c78923a4a5d614ada62/Untitled%201.png)

![Untitled](Practitioner%20Lab%20123%20SSRF%20via%20flawed%20request%20parsi%205f36ca9f26904c78923a4a5d614ada62/Untitled%202.png)

here I bruteforced it and found that .81 was valid.

through this I access the admin page. 

![Untitled](Practitioner%20Lab%20123%20SSRF%20via%20flawed%20request%20parsi%205f36ca9f26904c78923a4a5d614ada62/Untitled%203.png)

I opened this on the browser

and then captured the request and changed it to be valid and this deleted the user and solved the lab.

![Untitled](Practitioner%20Lab%20123%20SSRF%20via%20flawed%20request%20parsi%205f36ca9f26904c78923a4a5d614ada62/Untitled%204.png)