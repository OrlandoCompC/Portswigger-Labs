# Practitioner Lab 125: HTTP request smuggling, basic CL.TE vulnerability

---

This lab involves a front-end and back-end server, and the front-end server doesn't support chunked encoding. The front-end server rejects requests that aren't using the GET or POST method.

To solve the lab, smuggle a request to the back-end server, so that the next request processed by the back-end server appears to use the method `GPOST`.

### **Note**

Although the lab supports HTTP/2, the intended solution requires techniques that are only possible in HTTP/1. You can manually switch protocols in Burp Repeater from the **Request attributes** section of the **Inspector** panel.

### **Tip**

Manually fixing the length fields in request smuggling attacks can be tricky. Our [HTTP Request Smuggler](https://portswigger.net/blog/http-desync-attacks-request-smuggling-reborn#demo) Burp extension was designed to help. You can install it via the BApp Store.

![Untitled](Practitioner%20Lab%20125%20HTTP%20request%20smuggling,%20basic%20be26155cd0f64eb28b3657af9989c736/Untitled.png)

I went into inspector and changed the request to HTTP/1 .

I then added to the request the 

Transfer-Encoding: chunked
Content-Length: 27

This allowed me to then use the extension to send chunked data. 

![Untitled](Practitioner%20Lab%20125%20HTTP%20request%20smuggling,%20basic%20be26155cd0f64eb28b3657af9989c736/Untitled%201.png)

To see if its CLTE 

content length should be 6 

3

abc

X

If this times out its CLTE