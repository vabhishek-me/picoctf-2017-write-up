# Leaf of the Forest
---
### Question
We found an even bigger directory tree hiding a flag starting at /problems/b8c0c83a9aa6d7c4963d1bb09b9a33d0. It would be impossible to find the file named flag manually.

### HINTS

Is there a search function in Linux? Like if I wanted to 'find' something...

---
# Solution
If you are reading my writeup then i bet now you know the answer of this challenge because it's exactly same as [Leaf of the Tree](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/MISC/Leaf%20of%20the%20tree.md) the only difference is in leaf of the tree the directory was less like the only 1 tree but in the leaf of the forest you got too many directorys just like the compination of leafs of whole forest.

It's totally same so i am just writing my final payload. 
    ```bash
    $find /problems/b8c0c83a9aa6d7c4963d1bb09b9a33d0  -type f -name flag -exec     cat {} \;        ```
   
   And we will get the flag ```5a1555fd53f554bc846940b71e9f5e7```. Isn't it super easy?
   
   Thanks :) 
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

