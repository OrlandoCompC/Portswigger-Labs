# Practitioner Lab 55 :Blind SQL injection with conditional responses

---

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and no error messages are displayed. But the application includes a "Welcome back" message in the page if the query returns any rows.

The database contains a different table called `users`, with columns called `username` and `password`. You need to exploit the blind SQL injection vulnerability to find out the password of the `administrator` user.

To solve the lab, log in as the `administrator` user.

![Untitled](Practitioner%20Lab%2055%20Blind%20SQL%20injection%20with%20condi%200258b2803425442789b88d452a138609/Untitled.png)

I start by looking at the page.

I went into the cookies and put the injection 

I then went into intruder and made it find which one was 

![Untitled](Practitioner%20Lab%2055%20Blind%20SQL%20injection%20with%20condi%200258b2803425442789b88d452a138609/Untitled%201.png)

![Untitled](Practitioner%20Lab%2055%20Blind%20SQL%20injection%20with%20condi%200258b2803425442789b88d452a138609/Untitled%202.png)

And here is the answer.