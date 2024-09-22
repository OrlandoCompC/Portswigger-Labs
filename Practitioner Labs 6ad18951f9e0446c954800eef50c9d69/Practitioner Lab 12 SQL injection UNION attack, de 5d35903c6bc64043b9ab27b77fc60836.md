# Practitioner Lab 12: SQL injection UNION attack, determining the number of columns returned by the query

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values.

![Untitled](Practitioner%20Lab%2012%20SQL%20injection%20UNION%20attack,%20de%205d35903c6bc64043b9ab27b77fc60836/Untitled.png)

I open the page and see this, The first thing that comes to mind is that its dealing with the refine your search because this will end up querying the database.

![Untitled](Practitioner%20Lab%2012%20SQL%20injection%20UNION%20attack,%20de%205d35903c6bc64043b9ab27b77fc60836/Untitled%201.png)

I added the order by  to check how many columns it was querying. It gave me an error at 4 columns this letting me know that it had only  3 columns.

![Untitled](Practitioner%20Lab%2012%20SQL%20injection%20UNION%20attack,%20de%205d35903c6bc64043b9ab27b77fc60836/Untitled%202.png)

Here I just did it with the NULL and this resulted in the lab being completed because when you get the correct number of columns with NULL then you end up getting