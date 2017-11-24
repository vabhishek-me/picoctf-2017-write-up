# Digital Camouflage 
---
### Question

We need to gain access to some routers. Let's try and see if we can find the password in the captured network data: data.pcap.

### HINTS

It looks like someone logged in with their password earlier. Where would log in data be located in a network capture?
If you think you found the flag, but it doesn't work, consider that the data may be encrypted.

---

---
# Solution

It was also easy challenge. We just find the flag from the captured packets. I am going to solve it using ```wireshark``` 

1. So we got one ```.pcap``` file.
    ```bash
     data.pcap
    ```
2. Fire up it in your wireshark.
    ![promisechains](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/FORENSICS/first.png?raw=true "WireShark")

3. As you can see their are a lot of captured packets. Just analyise and at 98 you will get captured login packet(```Read: Hint```).Like this:-
Just ```right click on packet``` > ```Follow TCP Stream```

    ![promisechains](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/FORENSICS/second.png?raw=true "Follow TCP Stream")
   you will see somthing like this . As you can see in ```pswrd``` field their is something unique.  Its actually combination of Base64 and url encoding:- ```pswrd=cHJ2cUJaTnFZdw%3D%3D```
   
4. Lets decrypt:- 
   ```cHJ2cUJaTnFZdw%3D%3D``` > Decode url encoding: ```cHJ2cUJaTnFZdw==``` > decode base64: ```prvqBZNqYw```

    and we got the flag
    ```bash
    prvqBZNqYw
    ```
   Thanks :) 
   
   [@spiritedwolf](github.com/spiritedwolf)

---

