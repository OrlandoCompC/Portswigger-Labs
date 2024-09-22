# Practitioner Lab 65: Stored DOM XSS

---

This lab demonstrates a stored DOM vulnerability in the blog comment functionality. To solve this lab, exploit this vulnerability to call the `alert()` function.

![Untitled](Practitioner%20Lab%2065%20Stored%20DOM%20XSS%2045ade43d3d834b5eaabc9fcf8c1ab14e/Untitled.png)

Initially, my input was being encoded into html.

So the <> changed into the &lt; and &gt;

Knowing this I decided to try different types to bypass this. 

To do this I double URL encoded it, I changed it into base64, I converted it into hex. 

none of this worked but when I put both of them <<>> and this made some of them not be encoded. 

![Untitled](Practitioner%20Lab%2065%20Stored%20DOM%20XSS%2045ade43d3d834b5eaabc9fcf8c1ab14e/Untitled%201.png)

![Untitled](Practitioner%20Lab%2065%20Stored%20DOM%20XSS%2045ade43d3d834b5eaabc9fcf8c1ab14e/Untitled%202.png)

InnerHTML by standard doesn’t run script tags but if I use the image tag then it works

***HTML5 specifies that a <script> tag inserted with innerHTML should not execute.***

```
<>tlvfwind<img src='x' onerror='alert(1)'>
```

This solved the lab.