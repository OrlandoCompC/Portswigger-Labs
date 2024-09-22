# Practitioner Lab 107: Basic server-side template injection

---

This lab is vulnerable to server-side template injection due to the unsafe construction of an ERB template.

To solve the lab, review the ERB documentation to find out how to execute arbitrary code, then delete the `morale.txt` file from Carlos's home directory.

![Untitled](Practitioner%20Lab%20107%20Basic%20server-side%20template%20in%208490d570dd994c99a1fea44d67fe2093/Untitled.png)

When I try to open this page it says the following. I may be able to use this to do a template injection.

![Untitled](Practitioner%20Lab%20107%20Basic%20server-side%20template%20in%208490d570dd994c99a1fea44d67fe2093/Untitled%201.png)

By looking at the URL I can see where I could possibly do the injection. 

after using the following payload trying to see if I got an error 

```
<%=foobar%>
```

I got the following error telling me it was ruby

![Untitled](Practitioner%20Lab%20107%20Basic%20server-side%20template%20in%208490d570dd994c99a1fea44d67fe2093/Untitled%202.png)

When using ERB you wanna try and inject something like

`<%= x %>` to see if it comes to screen

![Untitled](Practitioner%20Lab%20107%20Basic%20server-side%20template%20in%208490d570dd994c99a1fea44d67fe2093/Untitled%203.png)

When I did this is gave me the value of 49 

I then searched how to delete a file on ruby template and found the File.delete and I tried to use it here and it worked. 

```
<%=File.delete("/home/carlos/morale.txt")%>
```

This solved the lab. 

Another solution would be to use the system method.

```
<%= system("rm /home/carlos/morale.txt") %>
```

URL-encode your payload and insert it