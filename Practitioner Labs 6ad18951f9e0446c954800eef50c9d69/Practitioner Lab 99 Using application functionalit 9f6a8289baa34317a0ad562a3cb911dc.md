# Practitioner Lab 99: Using application functionality to exploit insecure deserialization

---

This lab uses a serialization-based session mechanism. A certain feature invokes a dangerous method on data provided in a serialized object. To solve the lab, edit the serialized object in the session cookie and use it to delete the `morale.txt` file from Carlos's home directory.

You can log in to your own account using the following credentials: `wiener:peter`

You also have access to a backup account: `gregg:rosebud`

```
O:4:"User":3:{s:8:"username";s:6:"carlos";s:12:"access_token";i:0;s:11:"avatar_link";s:19:"users/carlos/morale.txt";}
```

In my first attempt I try to delete the account of the user which would then also delete the file.

on my next attemp if this doesn’t work then I will try to delete my account but at the same time delete their file.

![Untitled](Practitioner%20Lab%2099%20Using%20application%20functionalit%209f6a8289baa34317a0ad562a3cb911dc/Untitled.png)

It doesn’t let me change the token to carlos token to delete his account completely so I will have to use my account 

```
O:4:"User":3:{s:8:"username";s:6:"wiener";s:12:"access_token";s:32:"eofa3gzwj18nbchzapud14ygfsmor3yt";s:11:"avatar_link";s:23:"users/carlos/morale.txt";}
```

I changed the path of the avatar link to what might be the path of the file that carlos has.

This payload did not work because the file was not part of the avatar.

```
O:4:"User":3:{s:8:"username";s:6:"wiener";s:12:"access_token";s:32:"eofa3gzwj18nbchzapud14ygfsmor3yt";s:11:"avatar_link";s:10:"morale.txt";}
```

After reusing the following payload but changing the file path I was able to do it. 

**I found that I could reuse the same account even if it was already deleted.**

Another solution is this.