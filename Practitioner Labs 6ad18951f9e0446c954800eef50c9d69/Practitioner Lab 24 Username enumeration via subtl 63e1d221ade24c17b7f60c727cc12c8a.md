# Practitioner Lab 24: Username enumeration via subtly different responses

---

This lab is subtly vulnerable to username enumeration and password brute-force attacks. It has an account with a predictable username and password, which can be found in the following wordlists:

- Candidate usernames
- Candidate passwords

To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.

I got 2 wordlists for usernames and password. Now my first step would be to go into the login page and try to see if there are any reactions from the page that I can find to see if there is a correct username. 

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled.png)

In my first attempt I put a simple and short password to check the standard response times and the status codes. I did not find any weird HTTP status codes so my next plan was to go and see if I could find a response time that deviated. 

In order to do this I decided to put a very long password and see if there was any obvious change.

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%201.png)

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%202.png)

From what I found often the response time was around the 250 range but in this case for Carlos the response time was around 106. Even though this is a change I don’t believe this change is what is expected. I would imagine it would take longer than shorter because if the username is in fact valid then it would check the database.

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%203.png)

I redid the test and found an anomaly that did take longer. I will test this to see if is a valid username

Now I will run a test with the user atlas to see if I find a match

This did not work so I went into my next step which is to look fora slight difference. 

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%204.png)

I uses grep to see which ones had the message of Invalid username or password and then I got it.

This allowed me to see that the username was this one.

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%205.png)

![Untitled](Practitioner%20Lab%2024%20Username%20enumeration%20via%20subtl%2063e1d221ade24c17b7f60c727cc12c8a/Untitled%206.png)