# Practitioner Lab 51: Bypassing rate limits via race conditions

This lab's login mechanism uses rate limiting to defend against brute-force attacks. However, this can be bypassed due to a race condition.

To solve the lab:

1. Work out how to exploit the race condition to bypass the rate limit.
2. Successfully brute-force the password for the user `carlos`.
3. Log in and access the admin panel.
4. Delete the user `carlos`.

You can log in to your account with the following credentials: `wiener:peter`.

So I first looked at how many attempts it would take for me to get the account locked. 

I then used the burp turbo intruder to send multiple requests in one packet this way I would be able to send more requests at the same time thus bypassing the limit rate. 

![Untitled](Practitioner%20Lab%2051%20Bypassing%20rate%20limits%20via%20race%2029dbf7a1b8b24d298d2a6f396f54875d/Untitled.png)

Here I found the password

![Untitled](Practitioner%20Lab%2051%20Bypassing%20rate%20limits%20via%20race%2029dbf7a1b8b24d298d2a6f396f54875d/Untitled%201.png)

I learned that I could use the wordlist in my clipboard which was really cool when using burp turbo intruder.