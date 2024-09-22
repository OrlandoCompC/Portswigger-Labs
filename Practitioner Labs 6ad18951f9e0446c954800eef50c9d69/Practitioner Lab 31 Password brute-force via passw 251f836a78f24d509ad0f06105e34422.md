# Practitioner Lab 31: Password brute-force via password change

---

This lab's password change functionality makes it vulnerable to brute-force attacks. To solve the lab, use the list of candidate passwords to brute-force Carlos's account and access his "My account" page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`
- Candidate passwords

I started by looking at the functionality of the page. If the user was not valid username it would send me back into the login page.

if the username did not have a correct password then it would send me back into the login page also

My next step is to brute force the password using the username carlos.

![Untitled](Practitioner%20Lab%2031%20Password%20brute-force%20via%20passw%20251f836a78f24d509ad0f06105e34422/Untitled.png)

What I did was test the password change section and how it worked. 

Basically if you got the current password wrong it would log you out

but if you got the password write and the other 2 don’t match then you stay logged in and get an error message. So you have to be sure to check it out.