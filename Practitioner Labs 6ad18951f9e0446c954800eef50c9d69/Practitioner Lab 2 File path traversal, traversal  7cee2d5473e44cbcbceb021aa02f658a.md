# Practitioner Lab 2: File path traversal, traversal sequences stripped non-recursively

---

This lab contains a path traversal vulnerability in the display of product images.

The application strips path traversal sequences from the user-supplied filename before using it.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

![Untitled](Practitioner%20Lab%202%20File%20path%20traversal,%20traversal%20%207cee2d5473e44cbcbceb021aa02f658a/Untitled.png)

The first thing I do is look at the website and how it is working 

I see a lot of images so I can use Burpsuite to look at where are all these images coming from 

![Untitled](Practitioner%20Lab%202%20File%20path%20traversal,%20traversal%20%207cee2d5473e44cbcbceb021aa02f658a/Untitled%201.png)

Here I can see the request for all these images

I will try to change it for another file name to see if I can get it 

I know it is stripped so I will probably have to use // of them to get it to work.

![Untitled](Practitioner%20Lab%202%20File%20path%20traversal,%20traversal%20%207cee2d5473e44cbcbceb021aa02f658a/Untitled%202.png)

When I try to use the absolute path it doesn’t work because it is stripped.

Now I will use the double to see how it works 

![Untitled](Practitioner%20Lab%202%20File%20path%20traversal,%20traversal%20%207cee2d5473e44cbcbceb021aa02f658a/Untitled%203.png)

It took me a while but I figured out how it worked. This way it works when it is filtered.

![Untitled](Practitioner%20Lab%202%20File%20path%20traversal,%20traversal%20%207cee2d5473e44cbcbceb021aa02f658a/Untitled%204.png)