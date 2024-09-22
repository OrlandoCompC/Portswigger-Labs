# Practitioner Lab 35: Blind OS command injection with out-of-band data exfiltration

---

This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, execute the `whoami` command and exfiltrate the output via a DNS query to Burp Collaborator. You will need to enter the name of the current user to complete the lab.

I did a trial to see if it was vulnerable. I found that the fields: email,subject,message were vulnerable.

![Untitled](Practitioner%20Lab%2035%20Blind%20OS%20command%20injection%20wit%20fcfab3e32f6e450588fc0b5a00dd553c/Untitled.png)

here is the payload I sent

![Untitled](Practitioner%20Lab%2035%20Blind%20OS%20command%20injection%20wit%20fcfab3e32f6e450588fc0b5a00dd553c/Untitled%201.png)

Here is my collaborator server where it is getting the response.