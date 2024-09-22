# Practitioner Lab 37: Blind SQL injection with out-of-band data exfiltration

---

his lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The SQL query is executed asynchronously and has no effect on the application's response. However, you can trigger out-of-band interactions with an external domain.

The database contains a different table called `users`, with columns called `username` and `password`. You need to exploit the blind SQL injection vulnerability to find out the password of the `administrator` user.

To solve the lab, log in as the `administrator` user.

---

I start by going into the website and looking at the filtering system that they have in place. I get a request from it and do a deep dive into it. My first goal is to look if it is vulnerable and which type of database it is.

I quickly found it was an oracle database simply because I needed to use the FROM clause.

now that I know the database all I have to do is try to exfiltrate the data 

![Untitled](Practitioner%20Lab%2037%20Blind%20SQL%20injection%20with%20out-o%203a62fb2c6525472eb823ae3aa88e6181/Untitled.png)

I used a request for oracle to exfiltrate the data and send it to the collaborator

Using this I got the password for the admin user. 

![Untitled](Practitioner%20Lab%2037%20Blind%20SQL%20injection%20with%20out-o%203a62fb2c6525472eb823ae3aa88e6181/Untitled%201.png)

![Untitled](Practitioner%20Lab%2037%20Blind%20SQL%20injection%20with%20out-o%203a62fb2c6525472eb823ae3aa88e6181/Untitled%202.png)

And now all that is left is for me to sign in as the admin 

**2irp4gevlszc9psd6zh8**

![Untitled](Practitioner%20Lab%2037%20Blind%20SQL%20injection%20with%20out-o%203a62fb2c6525472eb823ae3aa88e6181/Untitled%203.png)