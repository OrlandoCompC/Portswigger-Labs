# Practitioner Lab 13: SQL injection UNION attack, finding a column containing text

---

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you first need to determine the number of columns returned by the query. You can do this using a technique you learned in a previous lab. The next step is to identify a column that is compatible with string data.

The lab will provide a random value that you need to make appear within the query results. To solve the lab, perform a SQL injection UNION attack that returns an additional row containing the value provided. This technique helps you determine which columns are compatible with string data.

![Untitled](Practitioner%20Lab%2013%20SQL%20injection%20UNION%20attack,%20fi%209c01f2f960df49eea937e13717fd3879/Untitled.png)

I found this table has 3 columns because the NULL did not give me an error.

![Untitled](Practitioner%20Lab%2013%20SQL%20injection%20UNION%20attack,%20fi%209c01f2f960df49eea937e13717fd3879/Untitled%201.png)

I found that the second column has a string Meaning that If I select from this row it should have the  value that I need.

![Untitled](Practitioner%20Lab%2013%20SQL%20injection%20UNION%20attack,%20fi%209c01f2f960df49eea937e13717fd3879/Untitled%202.png)

I solved the lab by selecting the whole value which is what the lab wanted.