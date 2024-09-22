# Practitioner Lab 104: Finding a hidden GraphQL endpoint

---

The user management functions for this lab are powered by a hidden GraphQL endpoint. You won't be able to find this endpoint by simply clicking pages in the site. The endpoint also has some defenses against introspection.

To solve the lab, find the hidden endpoint and delete `carlos`

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled.png)

Using  a GET request with url encoded parameters I was able to find the end point.

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%201.png)

Due to info disclosure I can then find the __schema or the __type and change it. By adding a space or a newline or a coma I might just bypass this. 

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%202.png)

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%203.png)

After sending the introspection response to repeter.

I found that there was a mutation

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%204.png)

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%205.png)

Using this I can delete carlos which is user 3 

![Untitled](Practitioner%20Lab%20104%20Finding%20a%20hidden%20GraphQL%20endp%200da8e263a4d24183929096fe1c0dbfea/Untitled%206.png)

User 3 was deleted and the lab was solved.