# Practitioner Lab 34:  Blind OS command injection with out-of-band interaction

---

I started by looking at which fields were vulnerable and found out that the email, subject and message field had  command injection vulnerabilities.

I then started by using nslookup ADDRESSOFCOLLABORATOR 

and this sent a request to the external server.

![Untitled](Practitioner%20Lab%2034%20Blind%20OS%20command%20injection%20wit%20d4e3018d3981486d9683887fdca7ce8c/Untitled.png)

![Untitled](Practitioner%20Lab%2034%20Blind%20OS%20command%20injection%20wit%20d4e3018d3981486d9683887fdca7ce8c/Untitled%201.png)

This solved the lab.