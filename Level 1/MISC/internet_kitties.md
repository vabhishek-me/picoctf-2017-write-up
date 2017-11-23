# Internet Kitties 
---
### Question

I was told there was something at IP shell2017.picoctf.com with port 2720. How do I get there? Do I need a ship for the port?

### HINTS

Look at using the netcat (nc) command!
To figure out how to use it, you can run "man nc" or "nc -h" on the shell, or search for it on the interwebz

---

---
# Solution

It was super easy challenge. Just read about the ```netcat``` or ```nc``` on the man page. 

1. So the question says we need to connect shell2017.picoctf.com to port 2720. 
    ```bash
    nc shell2017.picoctf.com 2720
    ```
    I think we got the flag.
    
    ```bash
    nc shell2017.picoctf.com  2720              
    Yay! You made it!
    Take a flag!
    0385d4bad438ffd596c049d5796e83a2
    ```
    
   Thanks :) 
   @spiritedwolf

---
