# Practitioner Lab 152: Client-side prototype pollution via browser APIs

---

This lab is vulnerable to DOM XSS via client-side prototype pollution. The website's developers have noticed a potential gadget and attempted to patch it. However, you can bypass the measures they've taken.

To solve the lab:

1. Find a source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that allows you to execute arbitrary JavaScript.
3. Combine these to call `alert()`.

You can solve this lab manually in your browser, or use DOM Invader to help you.

This lab is based on real-world vulnerabilities discovered by PortSwigger Research. For more details, check out Widespread prototype pollution gadgets by Gareth Heyes.

![Untitled](Practitioner%20Lab%20152%20Client-side%20prototype%20polluti%20e18edd4801814064a7df960d1b5bcb50/Untitled.png)

I started by seeing if I could inject a prototype. 

![Untitled](Practitioner%20Lab%20152%20Client-side%20prototype%20polluti%20e18edd4801814064a7df960d1b5bcb50/Untitled%201.png)

Dom invader found a sink and a gadget to inject xss

by looking at the code I can see the transport_url but it is blocked from being changed. 

![Untitled](Practitioner%20Lab%20152%20Client-side%20prototype%20polluti%20e18edd4801814064a7df960d1b5bcb50/Untitled%202.png)

The developers set transport_url to configurable false and writable false but I can still inject into the value.

They used the object.defineProperty but forgot to add an intial value which makes it vulnerable.

By using 

```
__proto__[value]=data:,alert(1)
```

this solved the lab