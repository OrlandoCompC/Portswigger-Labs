# Practitioner Lab 20: SQL injection with filter bypass via XML encoding

---

This lab contains a SQL injection vulnerability in its stock check feature. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables.

The database contains a `users` table, which contains the usernames and passwords of registered users. To solve the lab, perform a SQL injection attack to retrieve the admin user's credentials, then log in to their account.

I first had to get hackvector extension to be able to encode the SQL in a way that would bypass the firewall. 

Next, I had to use it to encode a simple command to get how many columns there was in the table 

![Untitled](Practitioner%20Lab%2020%20SQL%20injection%20with%20filter%20bypa%20e9319150e23444afa957681e053c49bb/Untitled.png)

If it returns null it means it worked, if it was an error it would give me no units.

![Untitled](Practitioner%20Lab%2020%20SQL%20injection%20with%20filter%20bypa%20e9319150e23444afa957681e053c49bb/Untitled%201.png)

Next, I used concatenation to get the username and password both in one.

![Untitled](Practitioner%20Lab%2020%20SQL%20injection%20with%20filter%20bypa%20e9319150e23444afa957681e053c49bb/Untitled%202.png)