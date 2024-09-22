# Practitioner Lab 108: Basic server-side template injection (code context)

---

This lab is vulnerable to server-side template injection due to the way it unsafely uses a Tornado template. To solve the lab, review the Tornado documentation to discover how to execute arbitrary code, then delete the `morale.txt` file from Carlos's home directory.

You can log in to your own account using the following credentials: `wiener:peter`

the first thing I tried was looking at the websites functionality and looked at how I could change my nickname. 

I then decided to post a comment as the user to see if my name would be reflected and it was. 

I then went into the account and changed the request to change a comment to see what would happen if I included the following string

```
${{<%[%'"}}%\
```

this resulted in a verbose error which told me information 

![Untitled](Practitioner%20Lab%20108%20Basic%20server-side%20template%20in%202f65776823c5418faf47d8b0f2655258/Untitled.png)

Now I will search for tornado to see how I can execute code in it.

when I use the 

```
{{7*7}}
```

This results in the application giving me a 49.

But if I try any of the others it results in an error. 

I noticed it was a code context based on the user.nickname

I now tried to break out of it and then inject more code. I this this by closing the user.nickname with }}

and then injecting the code after it .

```
user.nickname}}{% import os %}{{os.system('whoami')}}
```

this resulted in carlos being printed out on the screen. 

Now I could use this to remove the file. 

```
blog-post-author-display=user.nickname}}{% import os %}{{os.system('rm /home/carlos/morale.txt')}}
```

![Untitled](Practitioner%20Lab%20108%20Basic%20server-side%20template%20in%202f65776823c5418faf47d8b0f2655258/Untitled%201.png)