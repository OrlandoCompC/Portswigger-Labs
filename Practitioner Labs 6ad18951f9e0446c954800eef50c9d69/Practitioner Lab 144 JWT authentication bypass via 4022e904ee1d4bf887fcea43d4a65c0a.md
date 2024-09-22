# Practitioner Lab 144: JWT authentication bypass via weak signing key

---

This lab uses a JWT-based mechanism for handling sessions. It uses an extremely weak secret key to both sign and verify tokens. This can be easily brute-forced using a [wordlist of common secrets](https://github.com/wallarm/jwt-secrets/blob/master/jwt.secrets.list).

To solve the lab, first brute-force the website's secret key. Once you've obtained this, use it to sign a modified session token that gives you access to the admin panel at `/admin`, then delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled.png)

Using hashcat I was able to bruteforce the simple key

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%201.png)

It is secret1 

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%202.png)

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%203.png)

Loaded the secret key from a file and then it was solved. 

To do this on the JWT editor, you can do the following

encode the secret into base64 

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%204.png)

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%205.png)

use new symmetric key and click generate. then change the value of k for the base64 encoded secret.

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%206.png)

change the value click sign and then dont modify header. 

and then just send the request.

![Untitled](Practitioner%20Lab%20144%20JWT%20authentication%20bypass%20via%204022e904ee1d4bf887fcea43d4a65c0a/Untitled%207.png)

Easiest way is to go to recalculate and just put the secret there.