# Practitioner Lab 11: Remote code execution via polyglot web shell upload

---

This lab contains a vulnerable image upload function. Although it checks the contents of the file to verify that it is a genuine image, it is still possible to upload and execute server-side code.

To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled.png)

I first started by login in and looking how to upload an image .

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%201.png)

If I try to upload anything that is not an image then it says the following 

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%202.png)

if I upload an image it does this

I started by uploading an actual image and then slowly changed it into my PHP file by adding the .php but with a null byte at the end. I also added the script into it .

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%203.png)

and this did work but not exactly how I wanted . 

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%204.png)

None of this worked.

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%205.png)

I then decided to check other types and they didn’t work but the idea occurred that maybe it was just checking if there was a jpg it didn’t have to be in the end. so i made it .jpg.php

and this worked. 

giving me the code

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%206.png)

![Untitled](Practitioner%20Lab%2011%20Remote%20code%20execution%20via%20poly%2042769bb5dd16442eb84bcb86c78432d8/Untitled%207.png)