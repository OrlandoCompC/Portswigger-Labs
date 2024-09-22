# Practitioner Lab 50: Blind SSRF with out-of-band detection

---

This site uses analytics software which fetches the URL specified in the Referer header when a product page is loaded.

To solve the lab, use this functionality to cause an HTTP request to the public Burp Collaborator server.

![Untitled](Practitioner%20Lab%2050%20Blind%20SSRF%20with%20out-of-band%20de%20d65e6489d0c8443a8f61e46ca317c7ed/Untitled.png)

I used the collaborator as the referer URL which sent a DNS request there. This solved the lab.