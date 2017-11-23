# Leaf of the Tree
---
### Question

We found this annoyingly named directory tree starting at /problems/10f7c1d3e9fa2d4fc95555530ea97ec5. It would be pretty lame to type out all of those directory names but maybe there is something in there worth finding? And maybe we dont need to type out all those names...? Follow the trunk, using cat and ls!

### HINTS

Tab completion is a wonderful, wonderful thing

---

---
# Solution

It was also easy challenge. You can complete this challenge by checking-going in all folder manualy ```From-Hint:keep using tab button```. But we can use ```find``` command also. Just read about the ```find``` on it's the ```man``` page. 

1. So lets check what is inside the directory. 
    ```bash
    $cd /problems/10f7c1d3e9fa2d4fc95555530ea97ec5 && ls
   ~ trunk
    $cd trunk && ls
   ~trunkd091 
    ```
   So it keep showing us too many files lets use find command
    
    ```bash
    find -type $ -name $ -exec {}\;
    ```
    
    so here ```find``` is a command, ```-type``` is used to define which type of file we need to find so we will use ```f``` for finding regular file. Now ```-name``` here we need to give the file name and the last one ```-exec``` it is used  to execute commands and ```;``` will say end and return it. 
    
    so lets try
    ```bash
    $ find /problems/10f7c1d3e9fa2d4fc95555530ea97ec5 -type f -name  flag -exec cat {} \;                        
   88636e09e72bafb444e7f6a8105dbc5
    
    ```
    I think we got the flag ```88636e09e72bafb444e7f6a8105dbc5```
    
   Thanks :) 
   @spiritedwolf

---
