# Practitioner Lab 6: SSRF with blacklist-based input filter

---

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled.png)

I start by looking at the website itself and try to find if its communicating with the backend 

In this case it does this inside of the items they are selling to check if there are any items in stock 

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%201.png)

Now I will take a look at the request to see how it is working

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%202.png)

Here is the stock API which I can use to send request to the backend 

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%203.png)

I tried to access the /admin page using the trust of the [localhost](http://localhost) but it is blocked. 

It tells me that `External stock check blocked for security reasons.`

Now There are a few things I can do and I will try to do all the options I know

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%204.png)

I tried using 127.1 instead of 127.0.0.1 but it didn’t work. I also tried to URL encode it but it also didn’t work 

After trial and error, I found a solution to the problem

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%205.png)

If I used simply the loopback it would be blocked.

But if I used 127.1 it would pass meaning that it wasn’t only blacklisting the [localhost](http://localhost) but it was also blacklisting the admin word

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%206.png)

so I tried encoding the word admin but it didn’t work. Because of this I used double encoding to do it.

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%207.png)

This got me closer but if i double encode the whole word it doesn’t fully work so what if I encode only part of the word

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%208.png)

here i encoded the a

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%209.png)

Here I also double encoded the `a` with URL enconding.  This worked.

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%2010.png)

Now I captured the request to delete to add it to the original request 

/admin/delete?username=carlos

![Untitled](Practitioner%20Lab%206%20SSRF%20with%20blacklist-based%20input%20da1e74f4249c4a38808a78bb75494b48/Untitled%2011.png)