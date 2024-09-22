# Practitioner Lab 141: OAuth account hijacking via redirect_uri

---

This lab uses an OAuth service to allow users to log in with their social media account. A misconfiguration by the OAuth provider makes it possible for an attacker to steal authorization codes associated with other users' accounts.

To solve the lab, steal an authorization code associated with the admin user, then use it to access their account and delete the user `carlos`.

The admin user will open anything you send from the exploit server and they always have an active session with the OAuth service.

You can log in with your own social media account using the following credentials: `wiener:peter`.

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled.png)

I looked at this and saw the /auth with a redirect URI 

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled%201.png)

I also noticed this. Its redirecting to the URI so if I change it to the exploit server I could potentially get their token. 

I made a login request and intercepted, created a poc of that request and put it on my exploit server. 

I intercepted the request just to be safe. I was not sure if I could possibly reuse an older request. I did try to at one point but when I sent it, it would say it had already been used. 

and sent it. 

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled%202.png)

Here I checked the logs and found 

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled%203.png)

A valid token so now I make a request here. 

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled%204.png)

![Untitled](Practitioner%20Lab%20141%20OAuth%20account%20hijacking%20via%20r%209c7c389b7fae4be69f93f6c5860b3f56/Untitled%205.png)

Now im admin user and can delete carlos.

This solved the lab.

There was also no state here

It wouldve looked like this if it had a state 

```
GET /authorization?client_id=12345&redirect_uri=https://client-app.com/callback&response_type=code&scope=openid%20profile&state=ae13d489bd00e3c24 HTTP/1.1
Host: oauth-authorization-server.com
```