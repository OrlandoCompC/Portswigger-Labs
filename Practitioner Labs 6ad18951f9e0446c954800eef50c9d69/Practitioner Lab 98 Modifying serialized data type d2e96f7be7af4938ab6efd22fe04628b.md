# Practitioner Lab 98: Modifying serialized data types

---

This lab uses a serialization-based session mechanism and is vulnerable to authentication bypass as a result. To solve the lab, edit the serialized object in the session cookie to access the `administrator` account. Then, delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%2098%20Modifying%20serialized%20data%20type%20d2e96f7be7af4938ab6efd22fe04628b/Untitled.png)

While attempting to change the value I got some information disclosure. 

```
O:4:"User":2:{s:8:"username";s:13:"administrator";s:12:"access_token";i:0;}
```

After changing the cookie with the value of 0 for the access token this way it can be seen that the value is an integer and when this is compared to the access token for the admin then it will be true. which results in me gaining access.

![Untitled](Practitioner%20Lab%2098%20Modifying%20serialized%20data%20type%20d2e96f7be7af4938ab6efd22fe04628b/Untitled%201.png)

With this the lab was solved.