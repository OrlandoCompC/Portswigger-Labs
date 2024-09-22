# Practitioner Lab 84: SameSite Strict bypass via client-side redirect

---

This lab's change email function is vulnerable to CSRF. To solve the lab, perform a CSRF attack that changes the victim's email address. You should use the provided exploit server to host your attack.

You can log in to your own account using the following credentials: `wiener:peter`

I start this lab by going into the comment section to look at the email change functionality.

I will start by changing the email and looking at the request.

![Untitled](Practitioner%20Lab%2084%20SameSite%20Strict%20bypass%20via%20cli%200b126ce31dd54b50bccf08c233d8570a/Untitled.png)

As can be seen the sameSite is set to strict this means it won’t add cookies to any external requests.

I found the submit paramater set to 1 and set it to 0. to see what it does.

I noticed that when you post a comment  the website redirects you to the page where it confirms the comment has been successfully posted. 

Using this I try to do some path traversal through the URL to get to the myaccout and change the email.

![Untitled](Practitioner%20Lab%2084%20SameSite%20Strict%20bypass%20via%20cli%200b126ce31dd54b50bccf08c233d8570a/Untitled%201.png)

Here I can see it redirect still before redirecting me to the next page. 

![Untitled](Practitioner%20Lab%2084%20SameSite%20Strict%20bypass%20via%20cli%200b126ce31dd54b50bccf08c233d8570a/Untitled%202.png)

When I used this it took me to the home page 

![Untitled](Practitioner%20Lab%2084%20SameSite%20Strict%20bypass%20via%20cli%200b126ce31dd54b50bccf08c233d8570a/Untitled%203.png)

used this to go to the my-account and from here I did an email change.

using this payload 

```
<script>  
  document.location = "https://0ae8002d04eb51bc8321f57d00ed0019.web-security-academy.net/post/comment/confirmation?postId=1/../../my-account/change-email?email=changed@test&submit=1";
</script>
```

NEED TO URL ENCODE IT. IMPORTANT FOR THE @ as well as the &

I was able to solve the lab