# Practitioner Lab 1: File path traversal, traversal sequences blocked with absolute path bypass

---

This lab contains a path traversal vulnerability in the display of product images.

The application blocks traversal sequences but treats the supplied filename as being relative to a default working directory.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

![Untitled](Practitioner%20Lab%201%20File%20path%20traversal,%20traversal%20%20ac59163f995b4650ae0a86d4d341a7d3/Untitled.png)

I began by looking into one of these pages which have images

I then went into the source code and took a look at where the image was being accessed

![Untitled](Practitioner%20Lab%201%20File%20path%20traversal,%20traversal%20%20ac59163f995b4650ae0a86d4d341a7d3/Untitled%201.png)

I then went into it and change the image for the absolute path of the file `/etc/passwd` 

This then resulted in the lab being finished.

![Untitled](Practitioner%20Lab%201%20File%20path%20traversal,%20traversal%20%20ac59163f995b4650ae0a86d4d341a7d3/Untitled%202.png)

To solve this using Burp I went into the http history and this allowed me to see the request for images.

![Untitled](Practitioner%20Lab%201%20File%20path%20traversal,%20traversal%20%20ac59163f995b4650ae0a86d4d341a7d3/Untitled%203.png)

Here I take a look at the request and then change it to the absolute path of `/etc/passwd` and then I get the contents of the file 

![Untitled](Practitioner%20Lab%201%20File%20path%20traversal,%20traversal%20%20ac59163f995b4650ae0a86d4d341a7d3/Untitled%204.png)