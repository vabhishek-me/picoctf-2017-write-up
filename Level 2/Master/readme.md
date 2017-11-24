# Missing Identity
---
### Question
Turns out, some of the files back from Master Challenge 1 were corrupted. Restore this one file and find the flag. Update 16:26 EST 1 Apr If you feel that you are close, make a private piazza post with what you have, and an admin will help out. The flag starts with the character z.

### HINTS

What file is this?
What do you expect to find in the file structure?
All characters in the file are lower case or numberical. There will not be any zeros.

---
# Solution
So now lets to this master challenge of Level two. This challenge will open your door to ```Level 3```. This challenge was easy not that must hard. Just be focused and you will be be fine.

1. So we downloaded the [file](https://webshell2017.picoctf.com/static/bd42f889dd2015a6746e482cf350adb5/file)

2. Lets check which type of file it is:- 
    ```bash 
    $ file file
    file: data
    ```
3. Now lets do some enumeration.

   ```
   $strings file | more
    XXXXXX
    flag.png
    IHDR
    IDATx
    -6.V
    e~}e
    ->x>)
    hJwv0=
    q0yU
    ZY&Q
    `>=*U,
    jLNf
    jv@D
    v?kV
    {&p%
    aO~|<
    gs3'
    |~XS
    t_H%
    'Twl]Z
    -bD@
    e+*'
    }svZ
    300Jp
    0.NL
    PZIT
    _|k*
    @avT
    <r	(A(
    :Y,/
    JgZk
    IOo~
    F!Q(D
    p5uw
    tw>*
    /2330
    ndI+^_7Q
    &ghU
    --More--
   ```
   So just look at the starting ```XXXXXX``` it means invalid header is given and we can see the ```flag.png``` also lets copy this file ```file``` in ```.zip``` format.
   ```bash
   $cp file spirit.zip
   $unzip spirit.zip 
    Archive:  spirit.zip
    file #1:  bad zipfile offset (local header sig):  0
    inflating: nottheflag1.png         
    inflating: nottheflag2.png         
    inflating: nottheflag3.png         
    inflating: nottheflag4.png         
    inflating: nottheflag5.png         
    inflating: nottheflag6.png         
    inflating: nottheflag7.png    
   ```
4. So as you can see ```bad zipfile offset``` . So now lets open HexEditior and give the correct header offset. [Read This](https://www.garykessler.net/library/file_sigs.html)

    we need to change
    
    ```
    58 58 58 58 58 58 00 00 08 00 22 44 7F 4A B4 8B E4 67 2B 90 00 00 1C 90 00 00 08 00 00 00 66 6C 61 67 2E 70 6E 67 00 66 40 99 BF 89 50 4E 47 0D 0A 1A 0A 00 00 00 0D 49 48 44 52 00 00 02 81 00 00 00 3C 08 02 00 00 00 96 FA F7 6D 00 00 8F E3 49 44 41 54 78 9C EC FD 59 AF 6C D9 96 1E 86 8D 31 9B D5 45 1F BB 3F 6D B6 37 33 6F DE AE EA 96 CC 2A 56 D9 34 8B B2 20 1B 86 4C 91 80 21 D8 16 0C 43 06 FC E6 27 FD 0C C2 80 FC E2 27 FA C1 10 6C 58 76 D1 86 21 C0 B2 45 53 02 2D 36 2E 56 CB BA 75 9B 6C 4F BB FB 1D ED EA E6 9C 63 CE E1 87 15 11 3B 76 7B F6 3E 37 F3 B2 AA C8 C1 2C E2 DC 73 22 56 AC 66 AE 39 BA EF FB 06 9A F9 18 6E B6 DF FF 87 3F B1 73 57 BD E4 FF DE FF FA D7 6F F9 D8 BD EC FF F3 BF FB 93 E0 C2 CE 7F 2B FB CE 0F DF F9 67 BF F7 53 00 08 39 30 01 87 EB 3F 8F 02 9E FE AD C1 F1 17 53 00 A8 0F 7D 30 02 00 20 F0 EA 03 42 81 DE 86 CE 66 0C 00 BF F6 DF FD F4 96 9F 36 C6 FE D3 FF E3 4F A8 04 F0 97 FE 85 45 0A 18 A3 CE C0 1B 70 67 E7 FF 20 63 F1 BB FF AB 1F BD C5 65 FE 1B BB 6A BF F8 B3 2F 01 E0 A3 EF BF FF 6D 1C FC F7 FF E1 4F 3E F8 D1 C3 E1 E6 E0 8E 9F FF 83 FF FA 27 E3 9F DA CE BB B2 7C C1 DE DC B0 F8 EE 60 28 20 DA 82 EE 93 E4 DD 4F 1E F5 FA DD B7 3E CE BF B1 5F 8D FD D7 FF A7 3F F2 33 8E 06 C2 E5 C1 57 28 53 06 27 E3 5D 26 CB A1 86 BF F9 1F 7E 63 1B DD B7 6A AF 9E EF 3F 7A FA 00 00 FE C5 3F FC 33 57 FB BF FE 3F FC D1 9F FC 37 3F FD D1 EF 7C F7 97 39 E6 D1 FE C9 4F FF AB 97 00 E0 4B E0 EA E2 BF 09 44 C9 00 C0 1E 21 30 08 5C DF 81 65 0F 36 BE 93 FD F0 B7 3E FE 65 7E 7D 65 FF E5 FF F6 8F AE FE A5 EA 01 48 7E FF 77
    ---more---
    ```
    
    we need to change ```58 58 58 58 58 58``` to ```50 4B 03 04 00 00```
    
    and save the file as ```spirit-new.zip```
    
5. Just unzip
   ```bash
   $unzip spirit-new.zip
   Archive:  spirit-new.zip
   inflating: flag.png                
   inflating: nottheflag1.png         
   inflating: nottheflag2.png         
   inflating: nottheflag3.png         
   inflating: nottheflag4.png         
   inflating: nottheflag5.png         
   inflating: nottheflag6.png         
   inflating: nottheflag7.png 
   ```
   
   Just open the ```flag.png``` and you got the flag.
   
   ![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%202/Master/flag.png?raw=true)

   Thanks :) 
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

