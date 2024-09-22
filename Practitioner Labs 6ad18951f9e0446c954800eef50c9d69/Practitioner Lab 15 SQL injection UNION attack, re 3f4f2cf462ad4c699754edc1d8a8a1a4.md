# Practitioner Lab 15: SQL injection UNION attack, retrieving multiple values in a single column

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The database contains a different table called `users`, with columns called `username` and `password`.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the `administrator` user.

I start by going into the search area and look at the request. I also change the request to see how many columns the table has.

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled.png)

From here I know there are 2 columns. I will also now check if they are of string type.

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%201.png)

The first one gave me an error so it seems i

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%202.png)

One of the fields is a string but the other is not.

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%203.png)

I used this to see if I could get the username alone and it did. meaning that the password was not a string. 

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%204.png)

I used the fact that the username was a string to output more data into that one column.

and here I got the password for the admin 

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%205.png)

![Untitled](Practitioner%20Lab%2015%20SQL%20injection%20UNION%20attack,%20re%203f4f2cf462ad4c699754edc1d8a8a1a4/Untitled%206.png)

Here is the completed lab.