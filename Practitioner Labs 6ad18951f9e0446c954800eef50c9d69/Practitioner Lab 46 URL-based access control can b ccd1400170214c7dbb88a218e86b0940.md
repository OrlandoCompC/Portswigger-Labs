# Practitioner Lab 46: URL-based access control can be circumvented

---

This website has an unauthenticated admin panel at `/admin`, but a front-end system has been configured to block external access to that path. However, the back-end application is built on a framework that supports the `X-Original-URL` header.

To solve the lab, access the admin panel and delete the user `carlos`

![Untitled](Practitioner%20Lab%2046%20URL-based%20access%20control%20can%20b%20ccd1400170214c7dbb88a218e86b0940/Untitled.png)

I switched to /admin and then I used the url /admin/delete?username=carlos

![Untitled](Practitioner%20Lab%2046%20URL-based%20access%20control%20can%20b%20ccd1400170214c7dbb88a218e86b0940/Untitled%201.png)