# Practitioner Lab 22:  SQL injection attack, querying the database type and version on Oracle

---

This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled.png)

As soon as I enter the website I look for a SQL injection point. In this case It would be the search filter.  So I try to look at the request to see where I can inject SQL 

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%201.png)

By putting a ‘ on the URL is seems to give an Internal Server Error which means that I can do a SQL injection. 

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%202.png)

Here I am testing again to see if it is vulnerable and it seems that it is.

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%203.png)

After using ORDER BY I can tell that there are columns, my next step would be to see if they are both string. I would assume both are string because after looking at the output that the filter gives it seems that both are in fact string but I will check it anyways.

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%204.png)

Here this is giving me an error. The first thing that comes to mind is that this is an oracle database because I am missing the FROM. I can also see it on the expected output that the lab wants me to print to screen but I tried to not to look at that initially.

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%205.png)

Both columns are string. 

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%206.png)

Now I add the SELECT statement and it worked.

![Untitled](Practitioner%20Lab%2022%20SQL%20injection%20attack,%20querying%20e805a853fc944f34bca12ba93902e09c/Untitled%207.png)