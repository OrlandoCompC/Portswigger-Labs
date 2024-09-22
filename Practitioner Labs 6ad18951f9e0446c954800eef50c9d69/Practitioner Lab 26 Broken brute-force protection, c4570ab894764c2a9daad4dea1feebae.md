# Practitioner Lab 26: Broken brute-force protection, IP block

---

This lab is vulnerable due to a logic flaw in its password brute-force protection. To solve the lab, brute-force the victim's password, then log in and access their account page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`

On this lab, there is a brute-force protection that is implemented. The first thing that I want to do is to check how many tried before the account is locked. 

I did it on the repeater and after 4 attempts meaning that since I am getting an account I can login into the account and see if this resets the number of attempts I have made. 

![Untitled](Practitioner%20Lab%2026%20Broken%20brute-force%20protection,%20c4570ab894764c2a9daad4dea1feebae/Untitled.png)

 I used Turbo Intruder to get the password by making the account login every 2 failed attempts.

![Untitled](Practitioner%20Lab%2026%20Broken%20brute-force%20protection,%20c4570ab894764c2a9daad4dea1feebae/Untitled%201.png)