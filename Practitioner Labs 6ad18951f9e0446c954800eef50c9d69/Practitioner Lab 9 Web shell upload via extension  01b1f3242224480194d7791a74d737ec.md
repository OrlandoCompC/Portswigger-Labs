# Practitioner Lab 9: Web shell upload via extension blacklist bypass

---

This lab contains a vulnerable image upload function. Certain file extensions are blacklisted, but this defense can be bypassed due to a fundamental flaw in the configuration of this blacklist.

To solve the lab, upload a basic PHP web shell, then use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.

You can log in to your own account using the following credentials: `wiener:peter`

to start this lab I logged in as wiener 

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled.png)

This lab took me longer than I wanted. I didn’t understand how .htaccess worked very well but After doing some research I learned how it all worked and how it gives configurations for a particular directory.

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%201.png)

I knew it was an apache server because when I first did the post request it told me it was apache.

I went and made an .htaccess file

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%202.png)

This file basically tells the server that if it sees any .php5 to then run that file as if it was a php file.

When I initially uploaded this I made the mistake of uploading it using the ../  because I thought it needed to be in the previous directory. But after doing more research I found out that it needs to be in the same directory. 

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%203.png)

Here I am uploading the .htaccess file with the rule.

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%204.png)

Here I uploaded a .php5 file that would then be executed by the server as if it was a php file.

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%205.png)

I then saw this request which I used to execute the script. I sent this to repeater and there I executed the script

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%206.png)

Here the content was executed correctly and I got the flag

![Untitled](Practitioner%20Lab%209%20Web%20shell%20upload%20via%20extension%20%2001b1f3242224480194d7791a74d737ec/Untitled%207.png)

The lab is now Done.

I found this lab pretty tricky simply because even though I knew about .htaccess I didn’t fully understand how to use it. But now I have learned and hopefully won’t struggle as much with these labs.