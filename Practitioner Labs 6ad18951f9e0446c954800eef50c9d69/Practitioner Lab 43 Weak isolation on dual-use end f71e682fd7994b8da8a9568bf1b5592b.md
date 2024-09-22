# Practitioner Lab 43: Weak isolation on dual-use endpoint

---

This lab makes a flawed assumption about the user's privilege level based on their input. As a result, you can exploit the logic of its account management features to gain access to arbitrary users' accounts. To solve the lab, access the `administrator` account and delete the user `carlos`.

You can log in to your own account using the following credentials: `wiener:peter`

![Untitled](Practitioner%20Lab%2043%20Weak%20isolation%20on%20dual-use%20end%20f71e682fd7994b8da8a9568bf1b5592b/Untitled.png)

I took off the password field and it worked still. This means I don’t need the password to access another account

I can simply use the username of an admin user without the password.

![Untitled](Practitioner%20Lab%2043%20Weak%20isolation%20on%20dual-use%20end%20f71e682fd7994b8da8a9568bf1b5592b/Untitled%201.png)

![Untitled](Practitioner%20Lab%2043%20Weak%20isolation%20on%20dual-use%20end%20f71e682fd7994b8da8a9568bf1b5592b/Untitled%202.png)

![Untitled](Practitioner%20Lab%2043%20Weak%20isolation%20on%20dual-use%20end%20f71e682fd7994b8da8a9568bf1b5592b/Untitled%203.png)