# Practitioner Lab 33: Blind OS command injection with output redirection

---

This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. However, you can use output redirection to capture the output from the command. There is a writable folder at:

```
/var/www/images/
```

The application serves the images for the product catalog from this location. You can redirect the output from the injected command to a file in this folder, and then use the image loading URL to retrieve the contents of the file.

To solve the lab, execute the `whoami` command and retrieve the output.

i start by going into any of the pages and planning out my attack. 

I can see that the image is in /var/www/images and that it is using the `filename` meaning that I can probably do path traversal there. 

Into the form and send one to look at the request

the first thing I tried was a sleep command to see which field was vulnerable. I found that the email field was vulnerable again so I began working on it

![Untitled](Practitioner%20Lab%2033%20Blind%20OS%20command%20injection%20wit%2030a70297fa0a4adcb3d87e7ea977f247/Untitled.png)

I used this to go to the images directory and uploaded a file called exploit.txt

![Untitled](Practitioner%20Lab%2033%20Blind%20OS%20command%20injection%20wit%2030a70297fa0a4adcb3d87e7ea977f247/Untitled%201.png)

Lastly I got the information from the file using path traversal.

![Untitled](Practitioner%20Lab%2033%20Blind%20OS%20command%20injection%20wit%2030a70297fa0a4adcb3d87e7ea977f247/Untitled%202.png)

Here is my lab completed.