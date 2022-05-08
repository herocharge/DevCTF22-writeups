## Get Args

Nice little question.  

On running it asks for an input, and entering random gibberish gives wrong password or smtg of that sort.

I used `Ghidra` to solve it. I decompiled the program. This was the interesting part of the decompiled code.  

```c

    if (**(char **)(param_2 + 8) == '\0') {
      uVar3 = 0xffffffff;
    }
    else {
      for (local_24 = 0;
          ("AJi9VL0C4p"[local_24] != '\0' &&
          (*(char *)((long)local_24 + *(long *)(param_2 + 8)) != '\0')); local_24 = local_24 + 1) {
        cVar1 = "AJi9VL0C4p"[local_24];
        iVar2 = QM9Nq();
        if (cVar1 - iVar2 != (int)*(char *)((long)local_24 + *(long *)(param_2 + 8))) {
          printf("No, %s is not correct.\n",*(undefined8 *)(param_2 + 8));
          return 1;
        }
      }
      printf("Yes, %s is correct!\n",*(undefined8 *)(param_2 + 8));
      uVar3 = 0;
    }
  

```

It looks very complex, but the code is just looping over all the characters of our input and comparing it with a constant string `"AJi9VL0C4p"` with some offset.  
This offset is calculated with another function

```c
int QM9Nq(void)
{
  int local_1c;
  
  for (local_1c = 1; (local_1c < 0xb && (((local_1c % 0xb) * 4) % 0xb != 1));
      local_1c = local_1c + 1) {
  }
  return local_1c;
}
```

I didnt bother reading this code and just ran the code with gcc and it gave 3 as the output. So the offset is 3. The constant string  - 3 = our password.

A quick C program later, the password cameout to be `>Gf6SI-@1m` but we have to careful while entering as '>' is treated as output redirection. And the password was the flag if I remember correct.