# Practitioner Lab 58: Blind XXE with out-of-band interaction

---

his lab has a "Check stock" feature that parses XML input but does not display the result.

You can detect the blind XXE vulnerability by triggering out-of-band interactions with an external domain.

To solve the lab, use an external entity to make the XML parser issue a DNS lookup and HTTP request to Burp Collaborator.

![Untitled](Practitioner%20Lab%2058%20Blind%20XXE%20with%20out-of-band%20int%20e0c7ec03aafa4409bfadd5347131667a/Untitled.png)

It gave me an error but when I went into the collaborator I still got a response. 

Thus it means it worked. 

![Untitled](Practitioner%20Lab%2058%20Blind%20XXE%20with%20out-of-band%20int%20e0c7ec03aafa4409bfadd5347131667a/Untitled%201.png)

This completed the lab