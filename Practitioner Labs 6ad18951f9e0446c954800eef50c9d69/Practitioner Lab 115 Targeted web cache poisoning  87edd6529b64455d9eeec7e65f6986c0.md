# Practitioner Lab 115: Targeted web cache poisoning using an unknown header

---

This lab is vulnerable to web cache poisoning. A victim user will view any comments that you post. To solve this lab, you need to poison the cache with a response that executes `alert(document.cookie)` in the visitor's browser. However, you also need to make sure that the response is served to the specific subset of users to which the intended victim belong

![Untitled](Practitioner%20Lab%20115%20Targeted%20web%20cache%20poisoning%20%2087edd6529b64455d9eeec7e65f6986c0/Untitled.png)

Here I can see that the x-host is reflected in the response.

![Untitled](Practitioner%20Lab%20115%20Targeted%20web%20cache%20poisoning%20%2087edd6529b64455d9eeec7e65f6986c0/Untitled%201.png)

I can also see the vary header in the repsonse

The "Vary" HTTP header is used by the server to indicate which request headers, in addition to the URL, the server used to determine the response. This is typically used for caching purposes. When a cache sees the "Vary" header in a response, it takes into account the headers specified in its value in addition to the URL when deciding whether to serve a cached response for future requests.

What came to my mind was how would I get the user agent of the victim but then I remember that the victim can view all my comments. 

When you want to get the user to interact with a website and you can inject some type of html then the easiest is to use an image tag. 

```
<img src=website.com> 
```

other examples can also be using script tags if they are not blocked.

```
 <script>
    window.location.href = "https://www.example.com/new-page";
  </script>
  
  or
  
   <script>
    location = "https://www.example.com/new-page";
  </script>
```

using collaborator I was able to get the victims useragent. 

![Untitled](Practitioner%20Lab%20115%20Targeted%20web%20cache%20poisoning%20%2087edd6529b64455d9eeec7e65f6986c0/Untitled%202.png)

```
User-Agent: Mozilla/5.0 (Victim) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36
```

![Untitled](Practitioner%20Lab%20115%20Targeted%20web%20cache%20poisoning%20%2087edd6529b64455d9eeec7e65f6986c0/Untitled%203.png)

When testing i got the xss to work. Now I will change my user agent to that of the target to get them.

![Untitled](Practitioner%20Lab%20115%20Targeted%20web%20cache%20poisoning%20%2087edd6529b64455d9eeec7e65f6986c0/Untitled%204.png)

This solved it.