# Practitioner Lab 3: File path traversal, traversal sequences stripped with superfluous URL-decode

---

This lab contains a path traversal vulnerability in the display of product images.

The application blocks input containing path traversal sequences. It then performs a URL-decode of the input before using it.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

![Untitled](Practitioner%20Lab%203%20File%20path%20traversal,%20traversal%20%20800551f65e6346fcb230514f7f4d40ed/Untitled.png)

I started by looking around the page to see how it worked.

I then opened one of the images to see the request.

![Untitled](Practitioner%20Lab%203%20File%20path%20traversal,%20traversal%20%20800551f65e6346fcb230514f7f4d40ed/Untitled%201.png)

I looked at the request and then I changed it 

![Untitled](Practitioner%20Lab%203%20File%20path%20traversal,%20traversal%20%20800551f65e6346fcb230514f7f4d40ed/Untitled%202.png)

I had to encode it for it to work. 

and the lab is solved.

![Untitled](Practitioner%20Lab%203%20File%20path%20traversal,%20traversal%20%20800551f65e6346fcb230514f7f4d40ed/Untitled%203.png)