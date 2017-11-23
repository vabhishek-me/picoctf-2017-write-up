# computeAES
___

### Question

You found this clue laying around. Can you decrypt it?

### HINTS
Try online tools or python

### File contents
```
Encrypted with AES in ECB mode. All values base64 encoded
ciphertext = I300ryGVTXJVT803Sdt/KcOGlyPStZkeIHKapRjzwWf9+p7fIWkBnCWu/IWls+5S
key = iyq1bFDkirtGqiFz7OVi4A==
```

___

### Solution

The ciphertext is encrypted using AES ECB and then base64 encoded. Key is also base64 encoded.
You can do it using Python Packages like pycrypto.
But I used [OPENSSL](https://www.openssl.org/) command line tool.

Steps:

1. First decode the key from base64 to hex.
```
Key in base64 : iyq1bFDkirtGqiFz7OVi4A==
Key in Hex : 8B2AB56C50E48ABB46AA2173ECE562E0
```

2. Then copy the ciphertext to a file and run the following openssl command.
```bash
openssl enc -d -aes-128-ecb -in aesecbcipher.txt -out aesecbplain.txt -nopad -nosalt -K 8B2AB56C50E48ABB46AA2173ECE562E0 -iv 0 -base64
```

3. cat the aesecbplain.txt file.
```bash
cat aesecbplain.txt
flag{do_not_let_machines_win_2d4975bc}__________
```

### Tools

[OpenSSL](https://www.openssl.org/)

[base64 - Hex](http://tomeko.net/online_tools/base64.php?lang=en)


___
___

Thanks

Twitter : [@iammrdollar](https://twitter.com/iammrdollar)

Github : [@iammrdollar](https://github.com/iammrdollar)
