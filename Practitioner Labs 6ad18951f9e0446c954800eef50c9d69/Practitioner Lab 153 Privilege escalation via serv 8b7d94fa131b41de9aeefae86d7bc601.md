# Practitioner Lab 153: Privilege escalation via server-side prototype pollution

---

This lab is built on Node.js and the Express framework. It is vulnerable to server-side prototype pollution because it unsafely merges user-controllable input into a server-side JavaScript object. This is simple to detect because any polluted properties inherited via the prototype chain are visible in an HTTP response.

To solve the lab:

1. Find a prototype pollution source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that you can use to escalate your privileges.
3. Access the admin panel and delete the user `carlos`.

You can log in to your own account with the following credentials: `wiener:peter`

### **Note**

When testing for server-side prototype pollution, it's possible to break application functionality or even bring down the server completely. If this happens to your lab, you can manually restart the server using the button provided in the lab banner. Remember that you're unlikely to have this option when testing real websites, so you should always use caution.

The first thing I do when I start this page up is look at its functionality and how the site works. I know im looking for something that deals with json , preferably something that has some user data so that it can merge as such I log into the site.

![Untitled](Practitioner%20Lab%20153%20Privilege%20escalation%20via%20serv%208b7d94fa131b41de9aeefae86d7bc601/Untitled.png)

Here I capture this request and then look at how I can play with it to cause protype pollution.

![Untitled](Practitioner%20Lab%20153%20Privilege%20escalation%20via%20serv%208b7d94fa131b41de9aeefae86d7bc601/Untitled%201.png)

![Untitled](Practitioner%20Lab%20153%20Privilege%20escalation%20via%20serv%208b7d94fa131b41de9aeefae86d7bc601/Untitled%202.png)

While playing with the parameters I did this and it worked.  I was able to inject isAdmin=true 

```
 "__proto__":{
        "isAdmin":"true"
    }
```

![Untitled](Practitioner%20Lab%20153%20Privilege%20escalation%20via%20serv%208b7d94fa131b41de9aeefae86d7bc601/Untitled%203.png)

This successfully solved the lab.