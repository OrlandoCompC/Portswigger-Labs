# Practitioner Lab 96 : Manipulating the WebSocket handshake to exploit vulnerabilities

---

This online shop has a live chat feature implemented using [WebSockets](https://portswigger.net/web-security/websockets).

It has an aggressive but flawed XSS filter.

To solve the lab, use a WebSocket message to trigger an `alert()` popup in the support agent's browser.

![Untitled](Practitioner%20Lab%2096%20Manipulating%20the%20WebSocket%20han%20d7a95d47e359497391b9406219973aea/Untitled.png)

I can see the ip is blacklisted and I don’t know what attacks might work. My thought process right now is that I will have to use intruder and try but at the same time keep changing my ip in the X-Forwarded-For header.

the<img> tag is not blocked. 

When I add the <img src> it still works.

If I put onerror it gets blocked but if I put it in all capitals there is no issue. 

When I tried the <img src=1 ONERROR=’alert(1)’> it gave me an error 

So I will try to see if with the alert in capitals it works.

![Untitled](Practitioner%20Lab%2096%20Manipulating%20the%20WebSocket%20han%20d7a95d47e359497391b9406219973aea/Untitled%201.png)

This allowed me to reconnect after the IP was blacklisted.

![Untitled](Practitioner%20Lab%2096%20Manipulating%20the%20WebSocket%20han%20d7a95d47e359497391b9406219973aea/Untitled%202.png)

```

```

This payload solved it.

the alert has to be lowercase but the word itself was not being blacklisted instead it was the ()

this was not executing. Probably because is being sanitized. 

can put “encode”:false and then a normal payload works.