# Practitioner Lab 63: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

---

This lab contains a [DOM-based cross-site scripting](https://portswigger.net/web-security/cross-site-scripting/dom-based) vulnerability in a AngularJS expression within the search functionality.

AngularJS is a popular JavaScript library, which scans the contents of HTML nodes containing the `ng-app` attribute (also known as an AngularJS directive). When a directive is added to the HTML code, you can execute JavaScript expressions within double curly braces. This technique is useful when angle brackets are being encoded.

To solve this lab, perform a cross-site scripting attack that executes an AngularJS expression and calls the `alert` function.

![Untitled](Practitioner%20Lab%2063%20DOM%20XSS%20in%20AngularJS%20expressio%20c286c01f86054d409b0beff551e969a5/Untitled.png)

I can see the ng-app here. This means that there might be an angularjs vulnerability. 

```jsx
{{constructor.constructor('alert(1)')()}}
```

By using this payload I was able to get the alert and complete the lab

![Untitled](Practitioner%20Lab%2063%20DOM%20XSS%20in%20AngularJS%20expressio%20c286c01f86054d409b0beff551e969a5/Untitled%201.png)

![Untitled](Practitioner%20Lab%2063%20DOM%20XSS%20in%20AngularJS%20expressio%20c286c01f86054d409b0beff551e969a5/Untitled%202.png)