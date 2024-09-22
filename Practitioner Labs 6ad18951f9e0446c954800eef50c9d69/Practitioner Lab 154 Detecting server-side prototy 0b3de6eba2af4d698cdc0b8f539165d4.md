# Practitioner Lab 154: Detecting server-side prototype pollution without polluted property reflection

---

This lab is built on Node.js and the Express framework. It is vulnerable to server-side prototype pollution because it unsafely merges user-controllable input into a server-side JavaScript object.

To solve the lab, confirm the vulnerability by polluting `Object.prototype` in a way that triggers a noticeable but non-destructive change in the server's behavior. As this lab is designed to help you practice non-destructive detection techniques, you don't need to progress to exploitation.

You can log in to your own account with the following credentials: `wiener:peter`

### **Note**

When testing for server-side prototype pollution, it's possible to break application functionality or even bring down the server completely. If this happens to your lab, you can manually restart the server using the button provided in the lab banner. Remember that you're unlikely to have this option when testing real websites, so you should always use caution.

![Untitled](Practitioner%20Lab%20154%20Detecting%20server-side%20prototy%200b3de6eba2af4d698cdc0b8f539165d4/Untitled.png)

Made address_line1 have the value of foo but in UTF-7 

![Untitled](Practitioner%20Lab%20154%20Detecting%20server-side%20prototy%200b3de6eba2af4d698cdc0b8f539165d4/Untitled%201.png)

Changed the UTF to 7 this way it would ecode the foo and it did. 

This solved the lab. 

Another solution is :

![Untitled](Practitioner%20Lab%20154%20Detecting%20server-side%20prototy%200b3de6eba2af4d698cdc0b8f539165d4/Untitled%202.png)

![Untitled](Practitioner%20Lab%20154%20Detecting%20server-side%20prototy%200b3de6eba2af4d698cdc0b8f539165d4/Untitled%203.png)

![Untitled](Practitioner%20Lab%20154%20Detecting%20server-side%20prototy%200b3de6eba2af4d698cdc0b8f539165d4/Untitled%204.png)

If you look at the status it is now 555.