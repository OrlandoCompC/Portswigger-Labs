# Practitioner Lab 54: SQL injection attack, listing the database contents on non-Oracle databases

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The application has a login function, and the database contains a table that holds usernames and passwords. You need to determine the name of this table and the columns it contains, then retrieve the contents of the table to obtain the username and password of all users.

To solve the lab, log in as the `administrator` user.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled.png)

I start by looking at the filter. This is where the queries are sent to the database

Next I’ll put a ‘ to see if the page is vulnerable to SQL injection.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%201.png)

Since it gave a server side error it means it is vulnerable.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%202.png)

Now by looking at the normal data that the website has I can tell it has at least  2 columns which are text.

Next ill send the request to Burp and make sure.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%203.png)

The — worked so I can at the very least say it is not a mySQL database.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%204.png)

This worked which means it is not an oracle database because if it was I would require a FROM which in this case it is not present.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%205.png)

Now that I know the number of columns and that both accept text then I use this knowledge to get all the table names there.

This lets me know all the tables in the database.

From the output I can tell it is a a Postgres Database.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%206.png)

At the very bottom I found pg_user which is a table. Now using this table I will get all the columns which I can then use to get the username and password.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%207.png)

This will get me the columns 

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%208.png)

It gave me 2 users one of them is postgres which is the admin for the Postgres database but It is hashed. 

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%209.png)

Just to make sure this wasn’t a trick I made it output if it was really superuser.

I tried to use the default password for postgres which is postgres but this didn’t work 

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%2010.png)

I Noticed that the admin account for the database wouldn’t be the same admin account for the website. 

So I decided to look elsewhere and found 

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%2011.png)

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%2012.png)

Here is the answer.

![Untitled](Practitioner%20Lab%2054%20SQL%20injection%20attack,%20listing%20%2001c922792c1748f1a2da2e85893e96b3/Untitled%2013.png)