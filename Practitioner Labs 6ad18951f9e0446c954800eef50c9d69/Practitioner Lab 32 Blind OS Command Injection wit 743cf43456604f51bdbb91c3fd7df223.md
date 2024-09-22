# Practitioner Lab 32: Blind OS Command Injection with time delays

---

This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response.

To solve the lab, exploit the blind OS command injection vulnerability to cause a 10 second delay.

```
command1; command2   # Execute command1 and then command2
command1 && command2 # Execute command2 only if command1 succeeds
command1 || command2 # Execute command2 only if command1 fails
command1 & command2  # Execute command1 in the background
command1 | command2  # Pipe the output of command1 into command2
```

I used this logic, I knew I had to insert the command somewhere I started to inject it into each of the parameters and found that when I did it on the email it would give me an error so because of this I used the || which allowed me to do the lab

![Untitled](Practitioner%20Lab%2032%20Blind%20OS%20Command%20Injection%20wit%20743cf43456604f51bdbb91c3fd7df223/Untitled.png)

This solved the lab.