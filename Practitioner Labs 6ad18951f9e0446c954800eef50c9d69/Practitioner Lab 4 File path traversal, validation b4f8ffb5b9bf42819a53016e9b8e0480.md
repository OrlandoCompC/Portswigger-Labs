# Practitioner Lab 4: File path traversal, validation of start of path

---

This lab contains a path traversal vulnerability in the display of product images.

The application transmits the full file path via a request parameter, and validates that the supplied path starts with the expected folder.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

![Untitled](Practitioner%20Lab%204%20File%20path%20traversal,%20validation%20b4f8ffb5b9bf42819a53016e9b8e0480/Untitled.png)

I began by going into the page with an image and captured the request.

I then opened Burp Suite and looked at the request and as the lab specified the request will not work unless it has the main path of `/var/www/images` 

![Untitled](Practitioner%20Lab%204%20File%20path%20traversal,%20validation%20b4f8ffb5b9bf42819a53016e9b8e0480/Untitled%201.png)

I tried to check what answer it would give me when I didn;t have the full path name just to learn.

![Untitled](Practitioner%20Lab%204%20File%20path%20traversal,%20validation%20b4f8ffb5b9bf42819a53016e9b8e0480/Untitled%202.png)

After putting a full path name it worked out including the starting point of `/var/www/images.`

Now the lab is solved.

![Untitled](Practitioner%20Lab%204%20File%20path%20traversal,%20validation%20b4f8ffb5b9bf42819a53016e9b8e0480/Untitled%203.png)