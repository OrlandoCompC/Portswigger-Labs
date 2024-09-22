# Practitioner Lab 41: Inconsistent handling of exceptional input

---

This lab doesn't adequately validate user input. You can exploit a logic flaw in its account registration process to gain access to administrative functionality. To solve the lab, access the admin panel and delete the user `carlos`.

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled.png)

If I try to make another administrator account it won’t let me.

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%201.png)

I tried to add multiple emails but it didn’t work. I tried it in the other order too.

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%202.png)

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%203.png)

Here I was able to get both emails in one .

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%204.png)

This one worked too but it is not an admin account.

I found there is a limit on how long the email field can be. Basically it takes the email up to that point meaning that if you put the @dontwannacry.com  there and the other email at the end it will only take this one.

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%205.png)

This will send the email to my address but it will look as it if it part of the [dontwannacry.com](http://dontwannacry.com) 

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%206.png)

![Untitled](Practitioner%20Lab%2041%20Inconsistent%20handling%20of%20excep%20b2131aefec5d404594cf97885ef5cd0a/Untitled%207.png)

Here I deleted carlos.