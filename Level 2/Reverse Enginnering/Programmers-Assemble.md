# Programmers Assemble
---
### Question
You found a text file with some really low level code. Some value at the beginning has been X'ed out. Can you figure out what should be there, to make main return the value 0x1? Submit the answer as a hexidecimal number, with no extraneous 0s. For example, the decimal number 2015 would be submitted as 0x7df, not 0x000007df

### HINTS

All of the commands can be found here along with what they do.
It may be useful to be able to run the code, with test values.

---
# Solution

This challenge was also based on assebly as the name it self says. You must have the basic knowledge of assembly. In this challenge x86 ASM is their. In hint section you also got the x86 ASM wikipedia link. Trust me it can help you a lot. Just read about stack instructions and you will be fine.

1. In this challenge we got one file with name: 
    ```
    assembly.s
    ```
2. So it is assembly file lets check what is written inside this (I moved my file from ```assembly.s``` to ```assembly-1.s```):

    ```assembly
    .global main
    main:
    mov $XXXXXXX, %eax
    mov $0, %ebx
    mov $0x8, %ecx
    loop:
    test %eax, %eax
    jz fin
    add %ecx, %ebx
    dec %eax
    jmp loop
    fin:
    cmp $0xb790, %ebx
    je good
    mov $0, %eax
    jmp end
    good:
    mov $1, %eax
    end:
    ret
    ```

3. Lets try to see what is happening in this x86 ASM file here line by line.

    ```assembly
    .global main
    ```
    It says ```start the main```.
    
    ```assembly
    main:
    mov $XXXXXXX, %eax    
    mov $0, %ebx          
    mov $0x8, %ecx        
    ```
    
    Here in main it's 
    ``` mov $XXXXXXX, %eax``` means move XXXXXXX into the ```EAX``` , 
    ```mov $0, %ebx``` it means move the returned value of 0 in the ```EBX``` and
    ```mov $0x8, %ecx``` it means move the 8 into the ```ECX```
    
    ```assembly
    loop:
    test %eax, %eax        
    jz fin                 
    add %ecx, %ebx         
    dec %eax               
    jmp loop               
    ```
    Now here inside the loop: 
    ```test``` is used for compairing, here it's checking if ```EAX == 0```. 
    ```jz fin``` jz or je is jump, here it's ```jumping to fin if EAX == 0```.
    ```add %ecx, %ebx``` it means else add ```ECX to EBX```.
    ```dec``` is used for ```decreasin``` here it means to decrease EAX.
    ```jmp loop``` it will again go back to our ```loop:```

    ```assembly
    fin:
    cmp $0xb790, %ebx      
    je good                
    mov $0, %eax           
    jmp end                
    ```
    
    Here inside the fin,
    ```cmp $0xb790, %ebx``` cmp is used for compairing here we need to convert hex into the decimal. So, ```0xb790``` in decimal is ```46992``` so the line means ```if EAX = 46992```.
    ```je good``` as i told earlier je means jump so if EAX = 46992 then jump to good.
    ```mov $0, %eax``` else, move the returned value of 0 to EAX.
    ```jmp end``` and jumps to end.
    
    ```assembly
    good:
    mov $1, %eax           
    ```
    Here inside the good it means move the returned value of 1 to EAX. 
    
    ```assembly
    end:
    ret                     
    ```
   Means to exit the program.
   
   Now you all might be thinking what we need to do? Right? Actually we need to get into the good , so how we can we do it? as you can see under fin, its saying it will jump to good only if ```EAX = 46992```. So, how we can get to fin? See the ```loop```. 
   
   Lets focus and try to use our brain, 
   For accessing good we must have to get inside fin, and for accessing fin we must need to make the loop condition true. 
   
   ```good``` > ```fin``` > ```loop```
   
   So, inside loop it will call ```%eax``` for compairing if we will make it equals to 0 then we will get into the fin else it will do:
   ```%ebx += %ecx``` and ```%eax -=1```
   
   So i think you have understad what i mean to say, 
   
   Now we need to do something that will add ```%ecx into %ebx for %eax times```. Now lets check what what we have out of those 3 : We have ```%ecx``` which is ```0x8``` and we need to make ```%ebs = 0xb790```. Now we need to find the value of ```%eax```
   
   For it you can say ```%eax = %ebx/%ecx```. 
   
   So, ```46992/8 = 5874``` . We got our ```%eax``` which is equals to ```5874``` now convert this [decimal in hex](http://www.rapidtables.com/convert/number/decimal-to-hex.htm), 
   
   So we got ```$eax = 0x16F2```

So, i think we got the flag 
    ```
    0x16F2
    ```
     
     Hope you liked it :)
     
   ~Thanks
   
    [@spiritedwolf](https://github.com/spiritedwolf)

---

