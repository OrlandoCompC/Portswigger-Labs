# Practitioner Lab 160: Information disclosure in version control history

---

go to /.git and find a bunch of git files.

read them and then download. 

This shows the admin password was removed from the config. So I have to go back a commit. 

![Untitled](Practitioner%20Lab%20160%20Information%20disclosure%20in%20ver%20655a914b6a314119b1c255a521da56eb/Untitled.png)

I start with this

```
wget -r https://TARGET.web-security-academy.net/.git/
```

```
git-cola --repo TARGET.web-security-academy.net/
```

I then went into view, file broswer and found the files

![Untitled](Practitioner%20Lab%20160%20Information%20disclosure%20in%20ver%20655a914b6a314119b1c255a521da56eb/Untitled%201.png)

I then logged in and solved the lab.