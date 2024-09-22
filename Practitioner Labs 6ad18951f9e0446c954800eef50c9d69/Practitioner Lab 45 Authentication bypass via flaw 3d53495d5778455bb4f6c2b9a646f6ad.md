# Practitioner Lab 45: Authentication bypass via flawed state machine

---

This lab makes flawed assumptions about the sequence of events in the login process. To solve the lab, exploit this flaw to bypass the lab's authentication, access the admin interface, and delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

As the lab mentions the main issues occur in the login process so my first idea is to look at the full login process and see how it works.

![Untitled](Practitioner%20Lab%2045%20Authentication%20bypass%20via%20flaw%203d53495d5778455bb4f6c2b9a646f6ad/Untitled.png)

When you put your username and password this page comes up to choose. Now my plan is to test both and see how it reacts.

1 You enter credentials.

2 You select a role.

3 You gain access to the account.

I had to bypass the select role. Because the developer would assume that we have select a role and if you try to select blank it simply wouldn’t work. So by dropping the request and skipping it then I was able to to the admin user. 

![Untitled](Practitioner%20Lab%2045%20Authentication%20bypass%20via%20flaw%203d53495d5778455bb4f6c2b9a646f6ad/Untitled%201.png)

![Untitled](Practitioner%20Lab%2045%20Authentication%20bypass%20via%20flaw%203d53495d5778455bb4f6c2b9a646f6ad/Untitled%202.png)