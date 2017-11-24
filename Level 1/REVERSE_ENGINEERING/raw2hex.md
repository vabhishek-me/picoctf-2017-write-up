# Hex2Raw 
---
### Question

This program just prints a flag in raw form. All we need to do is convert the output to hex and we have it! CLI yourself to /problems/608e5f8b55c005ae6bc4ff13393c9c23 and turn that Raw2Hex!

### HINTS

Google is always very helpful in these circumstances. In this case, you should be looking for an easy solution.

---

# Solution

It was also a simple challenge like the first one. But in this challenge we just need to encode the value to hex as the challenger is saying. 

1. Lets check what are the files in the challenge directory.
        ```bash
        cd /problems/608e5f8b55c005ae6bc4ff13393c9c23
        ```
        I saw 4 files was their 
    ```
        flag  raw2hex
    ```
2. Just run the ```raw2hex``` binary.

    and we got the output
        
    ```bash
    The flag is:=C]Y+=|D2
    ```

3. so we need to encode it in the hex , now lets do it using ```cat and xxd xD```.
   first of all you must know how the cat command work in bash just simple man command can tell you everything. 
  
   we will use ```-d "the delimiter"``` and  ```-f "the fields"```
   ```bash
   cat -d ':' -f 2
   ```
    and for ```xxd``` we can use ```-p ``` "for getting output in plain hexdump style". Then just pipe all these out
    
    Well i think now we got the flag
    
    ```bash
    ~./raw2hex | cut -d ':' -f 2 | xxd -p
    
    3dacd3435d59a4862b9ff83d7c44cd320a
    ```
   
   And we got the flag.

   Thanks :) 
   
   [@spiritedwolf](github.com/spiritedwolf)

---
