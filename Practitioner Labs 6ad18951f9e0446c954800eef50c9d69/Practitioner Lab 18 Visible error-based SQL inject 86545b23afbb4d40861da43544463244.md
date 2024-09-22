# Practitioner Lab 18: Visible error-based SQL injection

---

This lab contains a SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie. The results of the SQL query are not returned.

The database contains a different table called `users`, with columns called `username` and `password`. To solve the lab, find a way to leak the password for the `administrator` user, and then log in to their account.

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled.png)

Putting a ‘ doesn’t give a server side error 

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%201.png)

Putting a single quote gives me a server side error as well as It gives some extra information. 

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%202.png)

If I put ‘’ it doesn’t give an error meaning that there is an SQL vulnerability.

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%203.png)

This worked meaning that it is not oracle because I didn’t need to use the FROM.

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%204.png)

This tells me that I am selecting in the WHERE clause.

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%205.png)

From doing this I can tell it is Postgres or else it would’ve given me an error 

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%206.png)

It seems as if my query is being cut off by a limit.

I erased the TrackingId and then used a cast query to see if i could get the username but Since I want it to show me an error I make it an Int This way it tells me which username I am getting 

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%207.png)

![Untitled](Practitioner%20Lab%2018%20Visible%20error-based%20SQL%20inject%2086545b23afbb4d40861da43544463244/Untitled%208.png)

After getting the Admin message I knew that was the user I wanted so I then changed the query to the password and got the password.

```
'+AND+1=CAST((SELECT+password+FROM+users LIMIT 1)+as+int)--
```