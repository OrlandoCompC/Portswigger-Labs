# Practitioner Lab 62: DOM XSS in document.write sink using source location.search inside a select element

---

This lab contains a [DOM-based cross-site scripting](https://portswigger.net/web-security/cross-site-scripting/dom-based) vulnerability in the stock checker functionality. It uses the JavaScript `document.write` function, which writes data out to the page. The `document.write` function is called with data from `location.search` which you can control using the website URL. The data is enclosed within a select element.

To solve this lab, perform a cross-site scripting attack that breaks out of the select element and calls the `alert` function.

You find a script in the inspector

![Untitled](Practitioner%20Lab%2062%20DOM%20XSS%20in%20document%20write%20sink%20b003f263986f4d7590d3bbb92fdef45c/Untitled.png)

Here you see that it is going into an image tag.

the [window.location.search](http://window.location.search) is anything after the query string.

I injected the following 

```
'lb55"><img src=0 onerror=alert(1)><!--'
```

Another thing that couldve been done is that since your already in the image.

```
lb155" onerror="alert(1)
```

Since the application adds one more then its solved.