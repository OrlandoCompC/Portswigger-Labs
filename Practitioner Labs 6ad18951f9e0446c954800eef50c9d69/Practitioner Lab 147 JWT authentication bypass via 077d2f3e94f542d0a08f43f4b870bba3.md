# Practitioner Lab 147: JWT authentication bypass via kid header path traversal

---

This lab uses a JWT-based mechanism for handling sessions. In order to verify the signature, the server uses the `kid` parameter in JWT header to fetch the relevant key from its filesystem.

To solve the lab, forge a JWT that gives you access to the admin panel at `/admin`, then delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

For this lab, I was able to use the kid to traverse.

I knew it supported symmetric algorithms because it had one set from the get go. HS256 (HMAC + SHA-256) use a "symmetric" key

I ended up having to create a new key and changing the value of the k in the key with the null byte in base64 which is equal to

```
AA==
```

after doing that I just started randomly adding a bunch of ../../../ until it worked.

I also had to sign the payload using this key. 

![Untitled](Practitioner%20Lab%20147%20JWT%20authentication%20bypass%20via%20077d2f3e94f542d0a08f43f4b870bba3/Untitled.png)