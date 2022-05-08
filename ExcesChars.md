## ExcessChars

It was pretty obvious from the title that this is going to be a bufferoverflow attack. But I have no experience with those.  
So I had to use an alternative approach.  
We had to trigger a function `printFlag()` which will then trigger another function `decryptAndPrint()`, calling the `decryptAndPrint()` directly with the use of gdb prints gibberish as the flag, I have no idea why. Calling `printFlag()` directly triggers an if statement which asks to not use gdb. It felt like a dead end, then I realised that I can modify the values of the memory from gdb. So I changed the flag variable used to trigger the if condition by setting $(eax) to 0.  
So I bypassed the if condition and I got the flag.

```
(gdb) p ($eax)
$1 = -1
(gdb) set ($eax)=0
(gdb) p ($eax)
$2 = 0
(gdb) n
Single stepping until exit from function ptrace,
which has no line number information.
printFlag () at crackme2.c:25
25	in crackme2.c
(gdb) n
Maybe you are in the right path ??

Flag you got is : 3xpl0!t_Rev3rs!nG_3G
```

We need to catch the ptrace function which is called to determine if the debugger is running or not. [Here's how](https://gist.github.com/poxyran/71a993d292eee10e95b4ff87066ea8f2)