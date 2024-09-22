# Practitioner Lab 122 : Routing-based SSRF

---

This lab is vulnerable to routing-based SSRF via the Host header. You can exploit this to access an insecure intranet admin panel located on an internal IP address.

To solve the lab, access the internal admin panel located in the `192.168.0.0/24` range, then delete the user `carlos`.

I started by changing the host header into my collaborator to see if was valid. 

it gave me a DNS request

![Untitled](Practitioner%20Lab%20122%20Routing-based%20SSRF%2082eb0c38f0d54d1294e2d95a70b12580/Untitled.png)

The lab provided me with the internal Ip address range so I changed it to a valid one through bruteforce. 

![Untitled](Practitioner%20Lab%20122%20Routing-based%20SSRF%2082eb0c38f0d54d1294e2d95a70b12580/Untitled%201.png)

This resulted in me being able to see how the admin panel looks.

I then opened this requests in my browser and I made a requests and intercepted it 

![Untitled](Practitioner%20Lab%20122%20Routing-based%20SSRF%2082eb0c38f0d54d1294e2d95a70b12580/Untitled%202.png)

This was a valid request which solved the lab. 

![Untitled](Practitioner%20Lab%20122%20Routing-based%20SSRF%2082eb0c38f0d54d1294e2d95a70b12580/Untitled%203.png)

Dont FORGET TO NOT HAVE THE ‘update host header to match target’ checked. If this is checked then It will keep changing your host header.