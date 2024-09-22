# Practitioner Lab 49: Referer-based access control

---

This lab controls access to certain admin functionality based on the Referer header. You can familiarize yourself with the admin panel by logging in using the credentials `administrator:admin`.

To solve the lab, log in using the credentials `wiener:peter` and exploit the flawed [access controls](https://portswigger.net/web-security/access-control) to promote yourself to become an administrator.

I captured the requests as an admin to see how they looked.

I then changed the request to be for the user wiener. I made sure the referer was coming from /admin that way I could bypass the firewall. 

![Untitled](Practitioner%20Lab%2049%20Referer-based%20access%20control%2013288c5e667246689c194b8a3a2aaf59/Untitled.png)