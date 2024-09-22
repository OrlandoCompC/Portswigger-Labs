# Practitioner Lab 126: HTTP request smuggling, basic TE.CL vulnerability

---

This lab involves a front-end and back-end server, and the back-end server doesn't support chunked encoding. The front-end server rejects requests that aren't using the GET or POST method.

To solve the lab, smuggle a request to the back-end server, so that the next request processed by the back-end server appears to use the method `GPOST`.

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled.png)

This request was valid telling me that it was a TECL

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled%201.png)

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled%202.png)

as can be seen on the right side the select size is 0x56 meaning that the size of the chunk is 56 

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled%203.png)

Content length is now 4 so I added so to the content length. 

The front end will check the chunk and the back end with check up to length 4 

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled%204.png)

The content length of the smuggled payload is 5 but I need to make it 6 so that it works because this way it will have an extra byte for the next part of the payload. 

![Untitled](Practitioner%20Lab%20126%20HTTP%20request%20smuggling,%20basic%20622937a2bfa9469689af67579e98275a/Untitled%205.png)

I will first send a malicious request then a normal request which will result in there being an error.

This solved the lab.

The reason why in this one you have to use the GPOST instead of just sending the G to append to the POST is because the 0 is also appended.