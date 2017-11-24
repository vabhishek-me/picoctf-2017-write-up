# Hex2Raw 
---
### Question

This program requires some unprintable characters as input... But how do you print unprintable characters? CLI yourself to /problems/b20c0c219ef2c830da927f80fb7e9cd3 and turn that Hex2Raw!

### HINTS

Google for easy techniques of getting raw output to command line. In this case, you should be looking for an easy solution.

---

---
# Solution

It was just a simple challenge. We just need inpute the decoded hex value. 

1. Lets check what are the files in the challenge directory.
      ```bash
       cd /problems/b20c0c219ef2c830da927f80fb7e9cd3
        ```
        I saw 4 files was their 
        ```
        flag  hex2raw  input
        ```
2. Just run the ```hex2raw```.

    and we got the output
    ```bash
    Give me this in raw form (0x41 -> 'A'):
    88a5e3d5caa34e85e5f36cd55d776568
    You gave me:
    ```

3. so we need to give the decoded value of hex, now lets decode it using ```echo```. But we need to put ```"\x"``` after every 2 bytes. Then just pipe you can simply execute your hex2raw binary.
   ```bash
   echo -e "\x88\xa5\xe3\xd5\xca\xa3\x4e\x85\xe5\xf3\x6c\xd5\x5d\x77\x65\x68"| ./hex2raw
   ```
    Well i think now we got the flag
    
  ```
  Give me this in raw form (0x41 -> 'A'):
  88a5e3d5caa34e85e5f36cd55d776568
  You gave me:
  88a5e3d5caa34e85e5f36cd55d776568
  Yay! That's what I wanted! Here be the flag:
  2bdd0a8259fcada3c12d732c7f3ca98a
  ```
   And we got the flag.

   Thanks :) 
   [@spiritedwolf](github.com/spiritedwolf)

---
