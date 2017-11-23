# Mystery Box
---
### Question
You've found a mystery machine with a sticky note attached to it! Oh, there's also this picture of the machine you found.

### HINTS

It really gets your gears Turing.
I hear there's something Naval about it.

---
# Solution
It was one of the crazy challenge for me. I had read the whole wikepedia page at that time. So we got two files 
```
note.txt Mysterybox.png
```

Actually the machine that is given in the MysterBox image is actually a cipher machine used by the germans.
![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%202/MISC/MysteryBox.png?raw=true)
 
 I got one great website [Engima Machine](http://enigma.louisedade.co.uk/enigma.html)
   
   In note.txt file these content was their
   ```
    Geheimnis: PXQQ TAMY YDBC WGYE LVN
    Umkehrwalze: B
    Grundstellung: PPP
    Ringstellung: LOG
    Steckerbrett: G-L, H-F
   ```
   
   so just fill it up
   ![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%202/MISC/Final.png?raw=true)
   
   and we got the flag just remove spaces from ```Cipher/Clear Text```
   
   ```Flag:QUITEPUZZLINGINDEED```
   
   ~Thanks
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

