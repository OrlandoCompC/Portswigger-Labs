# Practitioner Lab 30: Password reset poisoning via middleware

---

This lab is vulnerable to password reset poisoning. The user `carlos` will carelessly click on any links in emails that he receives. To solve the lab, log in to Carlos's account. You can log in to your own account using the following credentials: `wiener:peter`. Any emails sent to this account can be read via the email client on the exploit server.

The thing that comes to mind is to look at how the process works when you try to reset the password as a normal user. 

I started by going in as wiener, when I got the post to put the email I then redirected using the

X-Forwarded-Host to the exploit server 

I then looked at the logs that this server had and was able to see the token.

![Untitled](Practitioner%20Lab%2030%20Password%20reset%20poisoning%20via%20m%20f283fb6152f24521a4a10557fa4ef1cb/Untitled.png)

Here can be seen how I redirected the host.

This made the user connect to it.

![Untitled](Practitioner%20Lab%2030%20Password%20reset%20poisoning%20via%20m%20f283fb6152f24521a4a10557fa4ef1cb/Untitled%201.png)

Here can be seen the token of the victim carlos now I just need to reset his password and sign in.

`/forgot-password?temp-forgot-password-token=9uovy15o6keonfh0intjgme385sctk1o`

![Untitled](Practitioner%20Lab%2030%20Password%20reset%20poisoning%20via%20m%20f283fb6152f24521a4a10557fa4ef1cb/Untitled%202.png)

This allowed me to access the account and complete the lab.