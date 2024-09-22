# Practitioner Lab 23: SQL injection attack, listing the database contents on Oracle

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The application has a login function, and the database contains a table that holds usernames and passwords. You need to determine the name of this table and the columns it contains, then retrieve the contents of the table to obtain the username and password of all users.

To solve the lab, log in as the `administrator` user.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled.png)

The first thing I notice when I enter this lab is that there is a SQL query in the search filter. 

I could probably use this for a SQL injection.

The second thing I notice is the fact that there are at least  2 columns  which are both text due to the output.

My next step is to capture the request to truly know how many columns there are. 

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%201.png)

When I use a ‘ on the URL there is an internal server error which lets me know that the site might be vulnerable to an SQL injection.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%202.png)

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%203.png)

This lets me know that there are 2 columns, now I will test to see if it has 2 columns which are string.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%204.png)

Both of these fields are strings.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%205.png)

Now using this query I can see all the tables names and I will find the table that might have the users and passwords that I require.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%206.png)

This one is the one that calls my attention the most so I will start by looking at this one.

USERS_AONIUM

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%207.png)

I then used this query to get the column names from the table

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%208.png)

Here I found a column name called username and password so I will try to access the information that these columns have .

PASSWORD_WLPIGD

USERNAME_PGWFTI

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%209.png)

After using this query I can see the users at the bottom. Here I have the administrator password which I can use to sign in.

![Untitled](Practitioner%20Lab%2023%20SQL%20injection%20attack,%20listing%20%206875f2b9239d425986aff3337e7b00c2/Untitled%2010.png)

Now I signed in and the lab is complete.