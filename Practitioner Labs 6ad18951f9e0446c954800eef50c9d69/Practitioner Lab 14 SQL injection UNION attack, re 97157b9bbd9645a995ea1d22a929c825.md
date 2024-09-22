# Practitioner Lab 14: SQL injection UNION attack, retrieving data from other tables

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you need to combine some of the techniques you learned in previous labs.

The database contains a different table called `users`, with columns called `username` and `password`.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the `administrator` user.

![Untitled](Practitioner%20Lab%2014%20SQL%20injection%20UNION%20attack,%20re%2097157b9bbd9645a995ea1d22a929c825/Untitled.png)

I know it starts with the search bar. So I wanna see the response it gives.

![Untitled](Practitioner%20Lab%2014%20SQL%20injection%20UNION%20attack,%20re%2097157b9bbd9645a995ea1d22a929c825/Untitled%201.png)

At this point I know it is 2 columns and now I need to get the admin password

![Untitled](Practitioner%20Lab%2014%20SQL%20injection%20UNION%20attack,%20re%2097157b9bbd9645a995ea1d22a929c825/Untitled%202.png)

Here I got the username and password of the admin account

![Untitled](Practitioner%20Lab%2014%20SQL%20injection%20UNION%20attack,%20re%2097157b9bbd9645a995ea1d22a929c825/Untitled%203.png)

And here the lab is completed.