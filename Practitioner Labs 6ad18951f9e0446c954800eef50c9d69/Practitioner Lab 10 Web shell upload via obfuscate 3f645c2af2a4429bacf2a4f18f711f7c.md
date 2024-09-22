# Practitioner Lab 10: Web shell upload via obfuscated file extension

---

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed using a classic obfuscation technique.

To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled.png)

First thing I do is look around the page to see how it works and then go and login with the Wiener account 

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%201.png)

When I tried to upload a php file It gave me this message

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%202.png)

I attempted to upload a jpeg but it only wants jgp so I switched the content-type to jpg and it worked.

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%203.png)

I sent the php file with a different extension and it worked.

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%204.png)

Here I convinced the server that I was uploading a jpg but in truth it was a simple php file with a null byte. So the server takes it in as a .php 

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%205.png)

After this, I used a get request to get the flag and uploaded it and its done.

![Untitled](Practitioner%20Lab%2010%20Web%20shell%20upload%20via%20obfuscate%203f645c2af2a4429bacf2a4f18f711f7c/Untitled%206.png)