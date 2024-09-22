# Practitioner Lab 113 : Web cache poisoning with an unkeyed cookie

---

This lab is vulnerable to web cache poisoning because cookies aren't included in the cache key. An unsuspecting user regularly visits the site's home page. To solve this lab, poison the cache with a response that executes `alert(1)` in the visitor's browser.

![Untitled](Practitioner%20Lab%20113%20Web%20cache%20poisoning%20with%20an%20u%20cb2910b87b7f44139df923c98b50c920/Untitled.png)

here it points out that the cookie has a hidden paramater that is being cached. 

![Untitled](Practitioner%20Lab%20113%20Web%20cache%20poisoning%20with%20an%20u%20cb2910b87b7f44139df923c98b50c920/Untitled%201.png)

The fehost is reflected in the page. 

![Untitled](Practitioner%20Lab%20113%20Web%20cache%20poisoning%20with%20an%20u%20cb2910b87b7f44139df923c98b50c920/Untitled%202.png)

```
awdd"-alert(1)-"yes

a"}</script><img src=x onerror=alert(1)><script>data={"dwqdqwd
```

both oof these payloads work, I just wanted to have some fun. I tried the +alert(1)+ but this did not work because it was taking it as a space instead of concatenating. 

![Untitled](Practitioner%20Lab%20113%20Web%20cache%20poisoning%20with%20an%20u%20cb2910b87b7f44139df923c98b50c920/Untitled%203.png)

Which meant that when the user loaded the home page the image would try to load which would give an error and then give an alert()

![Untitled](Practitioner%20Lab%20113%20Web%20cache%20poisoning%20with%20an%20u%20cb2910b87b7f44139df923c98b50c920/Untitled%204.png)