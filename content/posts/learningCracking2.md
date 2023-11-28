+++
title = 'LearningCracking2'
date = 2023-11-28T13:14:39+13:00
draft: true
tags:
  - reverse_engineering
  - learning
  - crackmes.one
+++

### inxaneninja's Keygen Practice

1) Extract the zip using `crackmes.one`. We see a file called `license`. When I run it, it asks for a password. 

* Open this in Ghidra, we can see the main function and how the password function works. We can tell that it's C/C++. I added some comments to make it easier to read. (Comments reference the lines of code below.)

```c
undefined8 main(int param_1,undefined8 *param_2)

{
  char cVar1;
  undefined8 uVar2;
  size_t sVar3;
  size_t sVar4;
  int local_20;
  int local_1c;
  
  //param_2 is the password entered by the user

  if (param_1 < 2) {//if the number of arguments is less than 2, ask for a password input
    printf("Usage: %s <password>\n",*param_2);
    uVar2 = 1;
  }
  else {
    local_20 = 0;
    local_1c = 0;
    while( true ) {
        //sVar4 is the length of the provided password
        //all the casting here is because param_2 is undefined initially when passed in
      sVar4 = strlen((char *)param_2[1]);
      //if the length of the given password is equal to or less than local_1c (whose value is 0), exit the while loop and proceed to the next block of code. 
      
      //if this happens on the first loop, we won't get the correct password, because the value of local_20 will still be 0.

      if (sVar4 <= (ulong)(long)local_1c) break;
      //cVar1 = local_1c + password length.
      cVar1 = *(char *)((long)local_1c + param_2[1]);
      sVar4 = strlen((char *)param_2[1]); //not sure why this is calculated again here, since it's not used again in this block. could just be inaccuracy from decompilation. can ignore this.
      sVar3 = strlen((char *)param_2[1]);//sVar3 = password length
      //local_20 += cVar1 * sVar4 * sVar3
      //cVar1 = local_1c + password length
      //sVar4 = password length
      //sVar3 = password length
      local_20 = local_20 + (int)cVar1 * (int)sVar4 * (int)sVar3;
      //increment local_1c by 1 each loop
      local_1c = local_1c + 1;
    }
    if (local_20 == 0xcdaa) {//the decimal value of this is 52650
      puts("Good job!");
      uVar2 = 0;
    }
    else {
      puts("Wrong password!");
      uVar2 = 1;
    }
  }
  return uVar2;
}
```
* So we have learned that the proper way to generate a valid key to do the following:
  * the password length must be just right so that the following equation is valid. We'll denote password length as `p`:
    ```
    
    ```