# Practitioner Lab 150: Client-side prototype pollution via flawed sanitization

---

This lab is vulnerable to DOM XSS via client-side prototype pollution. Although the developers have implemented measures to prevent prototype pollution, these can be easily bypassed.

To solve the lab:

1. Find a source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that allows you to execute arbitrary JavaScript.
3. Combine these to call `alert()`.

![Untitled](Practitioner%20Lab%20150%20Client-side%20prototype%20polluti%20ed8aaf9f835e4d4ebf72414443ab3b18/Untitled.png)

I open the site and attempt to use the console to work with the commonly used prototype injections

```
/?__proto__.xlq6odlv=xlq6odlv
/?__proto__[xlq6odlv]=xlq6odlv
/?constructor.prototype.foo=bar

```

None of these worked. So I then tried to  look at the scripts to see what they had

I found the above script mentioning that constructor, _ _ proto _ _ is bad as well as prototype so the first thing that came to my mind was use something like

```
__pro__proto__to__.xlq6odlv=xlq6odlv
```

If the _ _ proto _ _ gets parsed the proto still stays as long as its not recursive 

![Untitled](Practitioner%20Lab%20150%20Client-side%20prototype%20polluti%20ed8aaf9f835e4d4ebf72414443ab3b18/Untitled%201.png)

Due to the parsing error of the website this did work.

as per the script. from what I can see what I have to inject is into the transport_url meaning id have to put something along the lines of [transport_url]=data:,alert(1)// 

![Untitled](Practitioner%20Lab%20150%20Client-side%20prototype%20polluti%20ed8aaf9f835e4d4ebf72414443ab3b18/Untitled%202.png)

the following payload worked

```
/?__pro__proto__to__[transport_url]=data:,alert(1)//
```

This solved the lab.