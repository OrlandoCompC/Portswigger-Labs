# Practitioner Lab 5:File path traversal, validation of file extension with null byte bypass

---

This lab contains a path traversal vulnerability in the display of product images.

The application validates that the supplied filename ends with the expected file extension.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

![Untitled](Practitioner%20Lab%205%20File%20path%20traversal,%20validation%20b22a94c15a18480d8aff1a91ff3df1c8/Untitled.png)

the first thing I do is check the website out and look for images. I will then click on the page with the image because this way I can see the request on Burp Suite

![Untitled](Practitioner%20Lab%205%20File%20path%20traversal,%20validation%20b22a94c15a18480d8aff1a91ff3df1c8/Untitled%201.png)

In this case, the server is checking for a specific extension so i put it after the %00 `null byte`

Now I am going to check how it works when I don’t put that. I want to see what type of answer it will give me.

![Untitled](Practitioner%20Lab%205%20File%20path%20traversal,%20validation%20b22a94c15a18480d8aff1a91ff3df1c8/Untitled%202.png)

It will simply say no such file.