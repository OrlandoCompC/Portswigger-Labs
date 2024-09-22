# Practitioner Lab 7: SSRF with filter bypass via open redirection vulnerability

---

This lab has a stock check feature which fetches data from an internal system.

The stock checker has been restricted to only access the local application, so you will need to find an open redirect affecting the application first.

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled.png)

I went into the page and looked at the check stock which accesses the database 

Here I took a look at the request to see what was happening and how it was working 

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled%201.png)

here I first check how it would react if I just tried to use the Ip directly without using local.

I will use their own URL and then &path=[http://192.168.0.12:8080/admin](http://192.168.0.12:8080/admin) to the end of the URL

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled%202.png)

As can be seen the URL doesn’t allow for redirections. 

I need a URL that needs redirections.

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled%203.png)

This URL allows for redirections I found this after clicking next item.

/product/nextProduct?currentProductId=1&path=/product?productId=2

I can use this URL and feed it to the stock checker to then be able to go to the admin page

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled%204.png)

I put the URL that I got before here to then be able to redirect to the Admin account 

![Untitled](Practitioner%20Lab%207%20SSRF%20with%20filter%20bypass%20via%20ope%20601c428d2e4e4fe1a3f737f1925f2fcf/Untitled%205.png)

I had to first encode it for it to really work because it is appended to the URL so it needs URL enconding.