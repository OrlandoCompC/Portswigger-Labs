# Practitioner Lab 117: Web cache poisoning via an unkeyed query parameter

---

This lab is vulnerable to web cache poisoning because it excludes a certain parameter from the cache key. A user regularly visits this site's home page using Chrome.

To solve the lab, poison the cache with a response that executes `alert(1)` in the victim's browser.

![Untitled](Practitioner%20Lab%20117%20Web%20cache%20poisoning%20via%20an%20un%2018210d56095646309f9060ed41dc0b2c/Untitled.png)

After checking it was caching regardless of how I changed the utm_content meaning that this could be used to exploit. 

![Untitled](Practitioner%20Lab%20117%20Web%20cache%20poisoning%20via%20an%20un%2018210d56095646309f9060ed41dc0b2c/Untitled%201.png)

Found it was being reflected.

This page is a cache oracle and I found a cache buster in the Origin. 

![Untitled](Practitioner%20Lab%20117%20Web%20cache%20poisoning%20via%20an%20un%2018210d56095646309f9060ed41dc0b2c/Untitled%202.png)

Found that this works so now I will try it without a cachebuster to deliver it to the victim.

![Untitled](Practitioner%20Lab%20117%20Web%20cache%20poisoning%20via%20an%20un%2018210d56095646309f9060ed41dc0b2c/Untitled%203.png)

This solved the lab.