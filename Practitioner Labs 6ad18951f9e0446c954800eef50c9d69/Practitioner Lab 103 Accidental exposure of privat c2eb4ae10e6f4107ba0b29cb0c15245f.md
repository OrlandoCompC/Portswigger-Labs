# Practitioner Lab 103: Accidental exposure of private GraphQL fields

---

The user management functions for this lab are powered by a GraphQL endpoint. The lab contains an [access control](https://portswigger.net/web-security/access-control) vulnerability whereby you can induce the API to reveal user credential fields.

To solve the lab, sign in as the administrator and delete the username `carlos`.

![Untitled](Practitioner%20Lab%20103%20Accidental%20exposure%20of%20privat%20c2eb4ae10e6f4107ba0b29cb0c15245f/Untitled.png)

I went in looking for some GraphQL queries and then found this. 

I then sent an introspective query to get the schema.

![Untitled](Practitioner%20Lab%20103%20Accidental%20exposure%20of%20privat%20c2eb4ae10e6f4107ba0b29cb0c15245f/Untitled%201.png)

Now I know to query getUser. I can change the Id to try and find to find the admin user.

![Untitled](Practitioner%20Lab%20103%20Accidental%20exposure%20of%20privat%20c2eb4ae10e6f4107ba0b29cb0c15245f/Untitled%202.png)

![Untitled](Practitioner%20Lab%20103%20Accidental%20exposure%20of%20privat%20c2eb4ae10e6f4107ba0b29cb0c15245f/Untitled%203.png)

After deleting the user the lab was solved.