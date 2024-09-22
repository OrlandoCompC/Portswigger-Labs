# Practitioner Lab 25: Username enumeration via response timing

---

This lab is vulnerable to username enumeration using its response times. To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.

- Your credentials: `wiener:peter`

For this lab I was given credentials. the first thing I will do is take a look at my account. I will sign in. In my mind I also have plans of maybe using this account to see how the response looks when I get a correct username.

When I tried to enumerate it gave me a message saying that I attempted to login too many times.

The first thing I tried was to try to brute force while logged in. 

This didn’t not work. Then I had to search how could I bypass the brute force limit and came upon the X-Forward. This didn’t work for me but the X-Foward-For:  this one worked for me. 

I then used this and a very long password and did it.

![Untitled](Practitioner%20Lab%2025%20Username%20enumeration%20via%20respo%20983af7fbec1b4658a4dea117268ac067/Untitled.png)

This gave me the user based on the response time.

![Untitled](Practitioner%20Lab%2025%20Username%20enumeration%20via%20respo%20983af7fbec1b4658a4dea117268ac067/Untitled%201.png)

I got 2 answers which seem like they could be a solution so I will try to enumerate both and see.

![Untitled](Practitioner%20Lab%2025%20Username%20enumeration%20via%20respo%20983af7fbec1b4658a4dea117268ac067/Untitled%202.png)

I tried the First one because the change was bigger and I found the password.

![Untitled](Practitioner%20Lab%2025%20Username%20enumeration%20via%20respo%20983af7fbec1b4658a4dea117268ac067/Untitled%203.png)