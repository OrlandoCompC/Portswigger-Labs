# Practitioner Lab 42: Low-level logic flaw

---

![Untitled](Practitioner%20Lab%2042%20Low-level%20logic%20flaw%20eeb785d55c804da5b36d384f5f2681c6/Untitled.png)

At one point the price becomes a negative number because it overflows.

The idea that comes to mind right now is to get it to become a negative number and then increase it slowly 

But I can decrease the price without limit.  But when increasing the quantity it can only be 99

![Untitled](Practitioner%20Lab%2042%20Low-level%20logic%20flaw%20eeb785d55c804da5b36d384f5f2681c6/Untitled%201.png)

At around this quantity it overflows.

![Untitled](Practitioner%20Lab%2042%20Low-level%20logic%20flaw%20eeb785d55c804da5b36d384f5f2681c6/Untitled%202.png)

By using multiple items I managed to get a good price that is below my limit.

![Untitled](Practitioner%20Lab%2042%20Low-level%20logic%20flaw%20eeb785d55c804da5b36d384f5f2681c6/Untitled%203.png)