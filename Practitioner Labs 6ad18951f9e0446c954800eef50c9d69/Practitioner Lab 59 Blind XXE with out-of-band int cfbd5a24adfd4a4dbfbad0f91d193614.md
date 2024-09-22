# Practitioner Lab 59: Blind XXE with out-of-band interaction via XML parameter entities

---

This lab has a "Check stock" feature that parses XML input, but does not display any unexpected values, and blocks requests containing regular external entities.

To solve the lab, use a parameter entity to make the XML parser issue a DNS lookup and HTTP request to Burp Collaborator.

![Untitled](Practitioner%20Lab%2059%20Blind%20XXE%20with%20out-of-band%20int%20cfbd5a24adfd4a4dbfbad0f91d193614/Untitled.png)

This is the payload I used. 

![Untitled](Practitioner%20Lab%2059%20Blind%20XXE%20with%20out-of-band%20int%20cfbd5a24adfd4a4dbfbad0f91d193614/Untitled%201.png)

This solved the lab.