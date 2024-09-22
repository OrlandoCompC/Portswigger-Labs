# Practitioner  Lab 44: Insufficient workflow validation

---

This lab makes flawed assumptions about the sequence of events in the purchasing workflow. To solve the lab, exploit this flaw to buy a "Lightweight l33t leather jacket".

You can log in to your own account using the following credentials: `wiener:peter`

The developer assumed the user will login, then go into the product page and add it to the cart, Lastly they would buy the item. But what if we try to buy an item without entering the users account. How would the system know the amount of funds we have to buy the item. 

This did not work. My next plan was to go into the other items. Buy a simple one and then see how I could get to the same page if I purchased the other. 

![Untitled](Practitioner%20Lab%2044%20Insufficient%20workflow%20validati%20d28220e083ad45e9b9f50e5a23d4da19/Untitled.png)