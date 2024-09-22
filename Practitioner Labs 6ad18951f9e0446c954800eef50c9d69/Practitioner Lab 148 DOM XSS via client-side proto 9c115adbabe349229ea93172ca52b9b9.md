# Practitioner Lab 148: DOM XSS via client-side prototype pollution

---

This lab is vulnerable to DOM XSS via client-side prototype pollution. To solve the lab:

1. Find a source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that allows you to execute arbitrary JavaScript.
3. Combine these to call `alert()`.

You can solve this lab manually in your browser, or use DOM Invader to help you.

The first thing I do is that when I enter the site I look at the functionality. 

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled.png)

I made dom invader do a full scan. 

I go through the site trying everything the site has so that dom invader can scan it.

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled%201.png)

Burp scanner was also able to find it. 

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled%202.png)

```
__proto__[transport_url]=data:,alert(1);//
```

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled%203.png)

By looking at the js file I found that they were using transport_url. This means I could inject a random url into this prototype or I could inject some xss like I did which solved the lab.

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled%204.png)

To test if its vulnerable. 

```
vulnerable-website.com/?__proto__[foo]=bar
```

Then go to the console and put

```
Object.prototype.foo
```

If it comes up with bar then its valid. 

In this one the reason why I dont use the **proto**….=alert(1) is because its expecting a link 

![Untitled](Practitioner%20Lab%20148%20DOM%20XSS%20via%20client-side%20proto%209c115adbabe349229ea93172ca52b9b9/Untitled%205.png)

so we feed it a data link