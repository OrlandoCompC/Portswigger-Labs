# Practitioner Lab 36: Blind SQL injection with out-of-band interaction

---

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The SQL query is executed asynchronously and has no effect on the application's response. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, exploit the SQL injection vulnerability to cause a DNS lookup to Burp Collaborator.

The first thing I do is look at the page and think where there could be an SQL vulnerabilty.

The most obvious one would be on the filter. I will capture that request and look at it in detail.

This was a simple lab where I just needed to get the request to the collaborator and it worked.

![Untitled](Practitioner%20Lab%2036%20Blind%20SQL%20injection%20with%20out-o%201ed6a5f8e7c642758e5f317fd2c7a9d9/Untitled.png)

This finished the lab.