# Practitioner Lab 138: HTTP/2 request splitting via CRLF injection

---

This lab is vulnerable to request smuggling because the front-end server downgrades HTTP/2 requests and fails to adequately sanitize incoming headers.

To solve the lab, delete the user `carlos` by using [response queue poisoning](https://portswigger.net/web-security/request-smuggling/advanced/response-queue-poisoning) to break into the admin panel at `/admin`. An admin user will log in approximately every 10 seconds.

The connection to the back-end is reset every 10 requests, so don't worry if you get it into a bad state - just send a few normal requests to get a fresh connection.

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled.png)

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%201.png)

Just me testing preparing for the exam. 

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%202.png)

Not giving me a 404

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%203.png)

Also not giving a 404 

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%204.png)

After adding it in a hidden way it still did not work.

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%205.png)

Adding this into the line I was able to smuggle the request.

I tried this **without adding the /r/n at the end** because in my mind the system could add it automatically.

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%206.png)

This has taken me a very long time

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%207.png)

Finally was able to get the admin cookie

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%208.png)

![Untitled](Practitioner%20Lab%20138%20HTTP%202%20request%20splitting%20via%20%2079c02988e4ed473abf1bdf44a77117a4/Untitled%209.png)