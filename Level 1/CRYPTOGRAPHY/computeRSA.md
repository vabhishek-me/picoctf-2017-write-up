# computeRSA
____

### Question

RSA encryption/decryption is based on a formula that anyone can find and use, as long as they know the values to plug in. Given the encrypted number 150815, d = 1941, and N = 435979, what is the decrypted number?

### Hint

decrypted = (encrypted) ^ d mod N

___

### Solution

The easiest. Open python and write
```ipython3
In [1]: (150815 ** 1941)%435979
Out[1]: 133337
```

___
___

Thanks

Twitter : [@iammrdollar](https://twitter.com/iammrdollar)

Github : [@iammrdollar](https://github.com/iammrdollar)
