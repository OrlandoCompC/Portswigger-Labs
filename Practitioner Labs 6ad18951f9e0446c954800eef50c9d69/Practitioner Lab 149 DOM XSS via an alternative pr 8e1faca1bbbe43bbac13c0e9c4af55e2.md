# Practitioner Lab 149: DOM XSS via an alternative prototype pollution vector

---

This lab is vulnerable to DOM XSS via client-side prototype pollution. To solve the lab:

1. Find a source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that allows you to execute arbitrary JavaScript.
3. Combine these to call `alert()`.

When I attempted to use

```
__proto__[foo]=bar
```

it did not work.

I then tried to use 

```
__proto__.foo=bar
```

and this worked. 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled.png)

I then decided to use a scan on dom invader. 

Thankfully burp scanner also found it which is something that will be a big help on the exam. 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%201.png)

After scanning for gadget, Dom Invader managed to find the gadget. 

I had already found it on my own but I wanted to make sure it was reliably found by dom invader. 

By looking at this Id have to exploit the sequence.

A good thing to know is that dom invader provides in between the canary, it provides the thing that needs to be exploited such as the sequence in this case. 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%202.png)

As can be seen in the picture on top after the canary, there seems to be a 1. this means that something is getting appended and is probably breaking the js. this means that after the payload we must include a - this way that part of the js continues . 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%203.png)

This works.

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%204.png)

This also works. 

After putting the normal payload. I see there is an error in the console 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%205.png)

I go to this error 

![Untitled](Practitioner%20Lab%20149%20DOM%20XSS%20via%20an%20alternative%20pr%208e1faca1bbbe43bbac13c0e9c4af55e2/Untitled%206.png)

here you can see the  alert(1)1 this is breaking the js which is whats making it not execute. 

```
__proto__.sequence=alert(1)-
__proto__.sequence=-alert(1)-
```