# Practitioner Lab 16: SQL injection attack, querying the database type and version on MySQL and Microsoft

---

This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.

The first thing I do is look at the request to the category filter.

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled.png)

Originally the standard order by and UNION SELECT NULL— was not working. This is because it is very likely a mySQL database. This means that I need to put a space at the end when using the —. 

I did this and found out that there were 2 columns 

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled%201.png)

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled%202.png)

I could have also used the #

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled%203.png)

Both columns seem to be string 

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled%204.png)

I ended up getting the version by using the version in one part and the  NULL on the other. This resulted in my having the answer at the very bottom.

![Untitled](Practitioner%20Lab%2016%20SQL%20injection%20attack,%20querying%2068f74596640b49998053bb179eab52d6/Untitled%205.png)

I was stuck on this one for a little bit, but the trick I found is to always go back to the basics. Basically start by finding out how many columns there are and which ones are string and keep going from there.