# Practitioner Lab 17: Blind SQL injection with conditional errors

---

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows. If the SQL query causes an error, then the application returns a custom error message.

The database contains a different table called `users`, with columns called `username` and `password`. You need to exploit the blind SQL injection vulnerability to find out the password of the `administrator` user.

To solve the lab, log in as the `administrator` user.

I start by opening the website and putting a ‘  on the categories but this worked normally so I went into the cookies and put one there and It still did not give me a response. 

I will now try to get a response from the server 

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled.png)

After I put just a single quote it gave me an internal error which means it might be vulnerable even though I already know its vulnerable.

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled%201.png)

When I do it with 2 quotes there is no issue as such I can say that it might be vulnerable

Now that I know that it is oracle I went and tried to find if the users table existed and it did then I used the same query but with a WHERE clause to find if the admin exists.

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled%202.png)

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled%203.png)

I used this query to find the length of the password. I ended up finding that it was 20 

Now I will try to find the password 

I will use intruder for this and iterate through all the characters of the password to find the solution

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled%204.png)

![Untitled](Practitioner%20Lab%2017%20Blind%20SQL%20injection%20with%20condi%20285df200db7049d9bf18e02ced62f113/Untitled%205.png)

The password was bsrmmjo4fvr7poelrdfk