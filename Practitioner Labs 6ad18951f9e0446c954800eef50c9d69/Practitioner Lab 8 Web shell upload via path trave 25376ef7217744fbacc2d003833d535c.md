# Practitioner Lab 8: Web shell upload via path traversal

---

This lab contains a vulnerable image upload function. The server is configured to prevent execution of user-supplied files, but this restriction can be bypassed by exploiting a secondary vulnerability.

To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled.png)

I start by going into the website with Burp Suite on. 

I checked all the requests

My first though it to try to upload a file even if it fails because it might give me some source code information as to where I could upload the file.

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%201.png)

When I did this it only sent me the contents of the file back it didn’t execute the script 

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%202.png)

While looking around I found a comment page where I can upload another image that might not be as secure.

This did not work because it was not allowing me to upload. My plan was to upload on my account and then come here and use the GET request to execute it but this was not working.

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%203.png)

I went back to upload the shell on my account. 

Here I used the ../ to go up a directory and be able to upload it there.

I tried it without encoding the characters but it wasn’t working so I had to URL encode it.

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%204.png)

It got uploaded to a directory up. 

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%205.png)

Now this is the GET request that I need to use to execute the file.

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%206.png)

Here is the file contents.

![Untitled](Practitioner%20Lab%208%20Web%20shell%20upload%20via%20path%20trave%2025376ef7217744fbacc2d003833d535c/Untitled%207.png)