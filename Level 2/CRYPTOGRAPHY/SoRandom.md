# SoRandom
___

### Question
We found sorandom.py running at shell2017.picoctf.com:63997. It seems to be outputting the flag but randomizing all the characters first. Is there anyway to get back the original flag?

### HINTS
How random can computers be?

### sorandom.py
```python2
#!/usr/bin/python -u
import random,string

flag = "FLAG:"+open("flag", "r").read()[:-1]
encflag = ""
random.seed("random")
for c in flag:
  if c.islower():
    #rotate number around alphabet a random amount
    encflag += chr((ord(c)-ord('a')+random.randrange(0,26))%26 + ord('a'))
  elif c.isupper():
    encflag += chr((ord(c)-ord('A')+random.randrange(0,26))%26 + ord('A'))
  elif c.isdigit():
    encflag += chr((ord(c)-ord('0')+random.randrange(0,10))%10 + ord('0'))
  else:
    encflag += c
print "Unguessably Randomized Flag: "+encflag
```

___

### Solution

#### netcat output
```bash
$ nc shell2017.picoctf.com 63997
Unguessably Randomized Flag: BNZQ:3o8b2bgl0689u4aj640407963277k0fc
```

Steps:

1. What this python program is doing is, it is using the string "random" as the seeder for random number generator. So, the random number generates a predefined set of numbers based on the seeder. 
Then it checks if the character is lowercase, uppercase or number.
Then it subtracts that character from its base character (like 'a', 'A', 0) and adds the random number between (0,26), then finds its modulus and adds the base again to find the ASCII value of the number. ord() converts ASCII character to ASCII number and chr() converts ASCII number to ASCII character.

2. I've written a program to reverse this logic. First, copy and paste the randomized flag ```BNZQ:3o8b2bgl0689u4aj640407963277k0fc``` to a file called ```encoded_flag```. Then run the program.

```python2
import string,random

flag = open("encoded_flag","r").read()
decoded = ""
randoms = [22, 2, 25, 10, 3, 11, 2, 22, 1, 25, 6, 9, 5, 0, 7, 4, 18, 7, 0, 5, 7, 7, 9, 7, 4, 6, 6, 5, 5, 8, 4, 7, 8, 1, 4, 1]

for c in flag:
  if c.islower():
    decoded += chr( ( (ord(c)-ord('a')) +26 -randoms.pop(0))%26 + ord('a'))
  elif c.isupper():
    decoded += chr( ( (ord(c)-ord('A')) +26 -randoms.pop(0))%26 + ord('A'))
  elif c.isdigit():
    decoded += chr( ( (ord(c)-ord('0')) +10-randoms.pop(0))%10 + ord('0'))
  else:
    decoded+=c

print "Check this out = " +decoded
```

3. Run the program.
```bash
$ python2 decode.py
Check this out = FLAG:0d6f1cac5615c7ae971761318430c9bb
```


___
___

Thanks

Twitter : [@iammrdollar](https://twitter.com/iammrdollar)

Github : [@iammrdollar](https://github.com/iammrdollar)
