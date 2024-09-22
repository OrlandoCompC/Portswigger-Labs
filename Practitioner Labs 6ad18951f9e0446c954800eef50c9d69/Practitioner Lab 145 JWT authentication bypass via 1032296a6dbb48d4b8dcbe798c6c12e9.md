# Practitioner Lab 145: JWT authentication bypass via jwk header injection

---

This lab uses a JWT-based mechanism for handling sessions. The server supports the `jwk` parameter in the JWT header. This is sometimes used to embed the correct verification key directly in the token. However, it fails to check whether the provided key came from a trusted source.

To solve the lab, modify and sign a JWT that gives you access to the admin panel at `/admin`, then delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

I tried the none headers. I then tried to see if I could embed a JWK with my own key to test if it would work. 

![Untitled](Practitioner%20Lab%20145%20JWT%20authentication%20bypass%20via%201032296a6dbb48d4b8dcbe798c6c12e9/Untitled.png)

came here and generated a new RSA key. 

I then went into the repeater changed my request how I wanted 

![Untitled](Practitioner%20Lab%20145%20JWT%20authentication%20bypass%20via%201032296a6dbb48d4b8dcbe798c6c12e9/Untitled%201.png)

I then when into attack and clicked embedded JWK. This then added some new fields and when I sent the request it worked. 

![Untitled](Practitioner%20Lab%20145%20JWT%20authentication%20bypass%20via%201032296a6dbb48d4b8dcbe798c6c12e9/Untitled%202.png)

![Untitled](Practitioner%20Lab%20145%20JWT%20authentication%20bypass%20via%201032296a6dbb48d4b8dcbe798c6c12e9/Untitled%203.png)

This solved the lab.