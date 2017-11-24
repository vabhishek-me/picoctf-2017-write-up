# A Thing Called the Stack
---
### Question
A friend was stacking dinner plates, and handed you this, saying something about a "stack". Can you find the difference between the value of esp at the end of the code, and the location of the saved return address? Assume a 32 bit system. Submit the answer as a hexidecimal number, with no extraneous 0s. For example, the decimal number 2015 would be submitted as 0x7df, not 0x000007df

### HINTS

Where is the return address saved on the stack?
Which commands actually affect the stack?

---
# Solution

1. It's one of the simple challenge if you know assembly, even just the basics. So we got a file ```assembly.c```

   ```assembly
    foo:
    pushl %ebp
    mov %esp, %ebp
    pushl %edi
    pushl %esi
    pushl %ebx
    sub $0xf8, %esp
    movl $0x1, (%esp)
    movl $0x2, 0x4(%esp)
    movl $0x3, 0x8(%esp)
    movl $0x4, 0xc(%esp)
  ```So, here we can see ```ebp,esp,edi,esi,ebx,esp``` are written. Which reaveals that it's 32Bit Assembly code. Lets 
  
 Here ```push %ebp pushl %edi pushl %esi pushl %ebx``` means just pushing whatever is in register EBP onto the stack
 ```mov %esp, %ebp``` takes the current stack pointer and uses it as the frame for the called function.
 
 So, it's pusshing 4 times and we know that each value is consist of 4 bytes. so means ```4*4=16```
 
 ```sub $0xf8, %esp``` means subtracts 0x000000f8 from ESP and it looks like this ```-4-4-4-4-f8``` . 
 
2. Now point here is what is 0xf8 just simply go to this [website](http://www.hexadecimaldictionary.com/hexadecimal/0xf8) to convert the 0xf8 to Decimal. Now ```0xf8``` is 248. Now add 16 to ```248+16=264```. Now convert decimal to hex using this [website](http://www.rapidtables.com/convert/number/decimal-to-hex.htm) 

3. So 264 is ```0x108``` so we got the flag.
 
 So, i think we got the flag.
  Hope you liked it
   ~Thanks
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

