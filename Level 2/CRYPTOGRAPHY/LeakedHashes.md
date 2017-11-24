# Shells
---
### Question
Someone got hacked! Check out some service's password hashes that were leaked at hashdump.txt! Do you think they chose strong passwords? We should check... The service is running at shell2017.picoctf.com:4145!

### HINTS

See if you can crack any of the login credentials and then connect to the service as one of the users. What's the chance these hashes have actually already been broken by someone else? Are there websites that host those cracked hashes? Connect from the shell with nc.

---
# Solution

It was the simples challenge. You just need to crack the hash.

In ```Hashdump.txt``` file we got this

```
root:be3f7de032d2e398ec542a7df71e0417
christene:08a81fafe787c93d02eb338b75f61819
nadia:b6eae1ba4ea6610cb0d12f0c21e1d2ec
myra:c213e8654b75ce017c9afb2c30e8c995
sharell:c213e8654b75ce017c9afb2c30e8c995
lilli:cead6186a16bf5486e5314ed8352d91e
ilene:89689941d40794e311ef8bc7061b9944
emiko:b6eae1ba4ea6610cb0d12f0c21e1d2ec
lindsey:e9ca957b80e51a398dd718a92da3060f
deandrea:edc1785161d271a14ad13098300e1431
honey:a28f30dd072b0aa66337f37526e7efa0
diana:74fe6370a9626ef1887c0e3ca4e6b600
lucretia:50f1d600b2257c7cfd44e568c63564c1
adelina:a64bb7fd1868a7bac23a384d014d352d
shala:96e68796a3b073205bb8d5688ded0934
jefferson:4dff179a4ec49e978ce72e6bf39b7d86
leandro:7b955cc1c21559338fdaf747434f3b36
lynwood:8922517b07c071e5dd9dd4932f6a3429
nikia:2ca54ed77f86e7ce73359e1c00debb1d
rickie:89689941d40794e311ef8bc7061b9944
kory:af33f8dc4c8602c7b6bbbbebe4ab5867
cordelia:08a81fafe787c93d02eb338b75f61819
hollie:c213e8654b75ce017c9afb2c30e8c995
lula:ac2f556a0eb415745b31e14a91d55d75
sara:3f4e535a671209f394817559372286f2
dede:96e68796a3b073205bb8d5688ded0934
jammie:435fc037deebaf8d9e3c4a4fb3e2fac7
kelvin:3a663354e45f1dbf9702ffa5dc799c2f
hildegard:a14ca920b8a9c1ee742b4248e7f9f56c
anabel:daae35de1f9c2cf09d95a99792dd7828
nathalie:d63d5efad4a59c06228d0596a89e2a34
jazmin:8922517b07c071e5dd9dd4932f6a3429
clinton:7afabc07ef7fc64e5cb8fce8dc07533e
gregg:ac2f556a0eb415745b31e14a91d55d75
sheilah:bd82f1bbabad9b7d12b3b183dc0cd0af
charity:96e68796a3b073205bb8d5688ded0934
roselyn:9ff497405dbd1cf3c17576629cf35475
denver:c213e8654b75ce017c9afb2c30e8c995
sonny:50f1d600b2257c7cfd44e568c63564c1
theresia:b6eae1ba4ea6610cb0d12f0c21e1d2ec
patience:0710f636e10edae58aea9a30125239ae
rita:b6eae1ba4ea6610cb0d12f0c21e1d2ec
karine:cc5847ba595f097885b2bbe5eb940e22
mariann:2cb699789d11d94fee780859adfabb91
tamela:cee42b4df8a585981a591220ece71c65
janett:96e68796a3b073205bb8d5688ded0934
maynard:41abf8a483960e48eaa199c00a68d833
luann:b51bc648f9d5e58971705b5efdc098a5
beau:0cd71c6a03a94e26e457dfb35b8e68d8
corrie:50f1d600b2257c7cfd44e568c63564c1
raina:1f5ff8608da1e56a59d1dff059286192
```

we can use cut command to print the hashes only.

```bash
 $cat hashdump.txt | cut -d ':' -f 2 > hashes.txt
 $cat hashes.txt
    be3f7de032d2e398ec542a7df71e0417
    08a81fafe787c93d02eb338b75f61819
    b6eae1ba4ea6610cb0d12f0c21e1d2ec
    c213e8654b75ce017c9afb2c30e8c995
    c213e8654b75ce017c9afb2c30e8c995
    cead6186a16bf5486e5314ed8352d91e
    89689941d40794e311ef8bc7061b9944
    b6eae1ba4ea6610cb0d12f0c21e1d2ec
    e9ca957b80e51a398dd718a92da3060f
    edc1785161d271a14ad13098300e1431
    a28f30dd072b0aa66337f37526e7efa0
    74fe6370a9626ef1887c0e3ca4e6b600
    50f1d600b2257c7cfd44e568c63564c1
    a64bb7fd1868a7bac23a384d014d352d
    96e68796a3b073205bb8d5688ded0934
    4dff179a4ec49e978ce72e6bf39b7d86
    7b955cc1c21559338fdaf747434f3b36
    8922517b07c071e5dd9dd4932f6a3429
    2ca54ed77f86e7ce73359e1c00debb1d
    89689941d40794e311ef8bc7061b9944
    af33f8dc4c8602c7b6bbbbebe4ab5867
    08a81fafe787c93d02eb338b75f61819
    c213e8654b75ce017c9afb2c30e8c995
    ac2f556a0eb415745b31e14a91d55d75
    3f4e535a671209f394817559372286f2
    96e68796a3b073205bb8d5688ded0934
    435fc037deebaf8d9e3c4a4fb3e2fac7
    3a663354e45f1dbf9702ffa5dc799c2f
    a14ca920b8a9c1ee742b4248e7f9f56c
    daae35de1f9c2cf09d95a99792dd7828
    d63d5efad4a59c06228d0596a89e2a34
    8922517b07c071e5dd9dd4932f6a3429
    7afabc07ef7fc64e5cb8fce8dc07533e
    ac2f556a0eb415745b31e14a91d55d75
    bd82f1bbabad9b7d12b3b183dc0cd0af
    96e68796a3b073205bb8d5688ded0934
    9ff497405dbd1cf3c17576629cf35475
    c213e8654b75ce017c9afb2c30e8c995
    50f1d600b2257c7cfd44e568c63564c1
    b6eae1ba4ea6610cb0d12f0c21e1d2ec
    0710f636e10edae58aea9a30125239ae
    b6eae1ba4ea6610cb0d12f0c21e1d2ec
    cc5847ba595f097885b2bbe5eb940e22
    2cb699789d11d94fee780859adfabb91
    cee42b4df8a585981a591220ece71c65
    96e68796a3b073205bb8d5688ded0934
    41abf8a483960e48eaa199c00a68d833
    b51bc648f9d5e58971705b5efdc098a5
    0cd71c6a03a94e26e457dfb35b8e68d8
    50f1d600b2257c7cfd44e568c63564c1
    1f5ff8608da1e56a59d1dff059286192
```

Go to hashkiller:- 
 and give these hashes their.
 and you will get output as
 
 ```
 be3f7de032d2e398ec542a7df71e0417 [Not found]
08a81fafe787c93d02eb338b75f61819 MD5 : d3r7h
b6eae1ba4ea6610cb0d12f0c21e1d2ec MD5 : w1l3w00ld
c213e8654b75ce017c9afb2c30e8c995 MD5 : c0nus
c213e8654b75ce017c9afb2c30e8c995 MD5 : c0nus
cead6186a16bf5486e5314ed8352d91e MD5 : 4ss37
89689941d40794e311ef8bc7061b9944 MD5 : 7h1ck
b6eae1ba4ea6610cb0d12f0c21e1d2ec MD5 : w1l3w00ld
e9ca957b80e51a398dd718a92da3060f MD5 : m3d14
edc1785161d271a14ad13098300e1431 MD5 : 0rr1s
a28f30dd072b0aa66337f37526e7efa0 MD5 : chumch0r3
74fe6370a9626ef1887c0e3ca4e6b600 MD5 : m4s7m3g4
50f1d600b2257c7cfd44e568c63564c1 MD5 : p4l1p4dg3
a64bb7fd1868a7bac23a384d014d352d MD5 : fr33d
96e68796a3b073205bb8d5688ded0934 MD5 : h4ugh
4dff179a4ec49e978ce72e6bf39b7d86 MD5 : s3r0w
7b955cc1c21559338fdaf747434f3b36 MD5 : r1gh7
8922517b07c071e5dd9dd4932f6a3429 MD5 : m4rch
2ca54ed77f86e7ce73359e1c00debb1d MD5 : sh3ll
89689941d40794e311ef8bc7061b9944 MD5 : 7h1ck
af33f8dc4c8602c7b6bbbbebe4ab5867 MD5 : 1n73r
08a81fafe787c93d02eb338b75f61819 MD5 : d3r7h
 ```
 
 Now just do nc and done.
 
 ```bash
 nc shell2017.picoctf.com 4145
enter username:
christene
christene's password:d3r7h
welcome to shady file server. would you like to access the cat ascii art database? y/n
y

     /\_/\ 
    ( o o )
  G-==_Y_==-M
      `-'
      
  /\ /\ 
  (O o)
=(: ^ :)=  
  '*v*'
  
 |\_/|     
 (. .)
  =w= (\   
 / ^ \//   
(|| ||)
,""_""_ .

     /\_/\ 
    ( o o )
   -==_Y_==- 
      `-'
    /\**/\ 
   ( o_o  )_)
   ,(u  u  ,),
  {}{}{}{}{}{}
  
  /\_/\ 
 ( o.o )
  > ^ <
  
       /\_/\ 
  /\  / o o \ 
 //\ \~(*)~/
 `  \/   ^ /
    | \|| ||  
    \ '|| ||  
     \)()-())
     
   A_A
  (-.-)
   |-|   
  /   \  
 |     |  __
 |  || | |  \___
 \_||_/_/
 
     /\__/\ 
    /`    '\ 
  === 0  0 ===
    \  --  /    - flag is ac09afa2fcc825a31b9a46bab6223dd3

   /        \ 
  /          \ 
 |            |
  \  ||  ||  /
   \_oo__oo_/#######o
   
  /\___/\ 
 ( o   o )
 (  =^=  ) 
 (        )
 (         )
 (          )))))))))))
 
 /\ /\ 
 (O o)
=(:^:)=  
   U
   
    _,,/|
    \o o' 
    =_~_=
    /   \ (\ 
   (////_)//
   ~~~
   
   /\     /\ 
  {  `---'  }
  {  O   O  }  
~~|~   V   ~|~~  
   \  \|/  /   
    `-----'__
    /     \  `^\_
   {       }\ |\_\_   W
   |  \_/  |/ /  \_\_( )
    \__/  /(_E     \__/
      (  /
       MM
       
              ("`-''-/").___..--''"`-._
               `6_ 6  )   `-.  (     ).`-.__.`)
               (_Y_.)'  ._   )  `._ `. ``-..-'
             _..`--'_..-_/  /--'_.' ,'
           (il),-''  (li),'  ((!.-'
           
from http://user.xmission.com/~emailbox/ascii_cats.htm

 ```
 
 So, i think we got the flag. ```flag is ac09afa2fcc825a31b9a46bab6223dd3```
  
  Hope you liked it
  
   ~Thanks
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

