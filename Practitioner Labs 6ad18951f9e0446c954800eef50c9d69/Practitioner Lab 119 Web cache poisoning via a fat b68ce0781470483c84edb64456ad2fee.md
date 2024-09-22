# Practitioner Lab 119: Web cache poisoning via a fat GET request

---

This lab is vulnerable to web cache poisoning. It accepts `GET` requests that have a body, but does not include the body in the cache key. A user regularly visits this site's home page using Chrome.

To solve the lab, poison the cache with a response that executes `alert(1)` in the victim's browser.

![Untitled](Practitioner%20Lab%20119%20Web%20cache%20poisoning%20via%20a%20fat%20b68ce0781470483c84edb64456ad2fee/Untitled.png)

![Untitled](Practitioner%20Lab%20119%20Web%20cache%20poisoning%20via%20a%20fat%20b68ce0781470483c84edb64456ad2fee/Untitled%201.png)

Using these I was able to make a sample request to the js to inject my own paramater. 

I saw that the homepage had a reference to the js file. So If I manage to poison it then I could potentially compromise the homepage.

![Untitled](Practitioner%20Lab%20119%20Web%20cache%20poisoning%20via%20a%20fat%20b68ce0781470483c84edb64456ad2fee/Untitled%202.png)

![Untitled](Practitioner%20Lab%20119%20Web%20cache%20poisoning%20via%20a%20fat%20b68ce0781470483c84edb64456ad2fee/Untitled%203.png)

After doing somme extra tests there was no need for the POST

![Untitled](Practitioner%20Lab%20119%20Web%20cache%20poisoning%20via%20a%20fat%20b68ce0781470483c84edb64456ad2fee/Untitled%204.png)

This also worked and solved the lab.