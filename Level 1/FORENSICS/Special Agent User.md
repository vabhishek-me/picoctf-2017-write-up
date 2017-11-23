# Special Agent User 
---
### Question

We can get into the Administrator's computer with a browser exploit. But first, we need to figure out what browser they're using. Perhaps this information is located in a network packet capture we took: data.pcap. Enter the browser and version as "BrowserName BrowserVersion". NOTE: We're just looking for up to 3 levels of subversions for the browser version (ie. Version 1.2.3 for Version 1.2.3.4) and ignore any 0th subversions (ie. 1.2 for 1.2.0)

### HINTS

Where can we find information on the browser in networking data? Maybe try reading up on user-agent strings.

---

---
# Solution

It was little tricky challenge. In this challenge we again got the ```.pcap``` files. I am going to do solve it using ```wireshark``` 

1. So we got one ```.pcap``` file.
    ```bash
     data.pcap
    ```
2. Fire up it in your wireshark.
    ![promisechains](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/FORENSICS/Agent-first.png?raw=true "WireShark")

3. As you can see their are a lot of captured packets. First read the hint and the question. Also check the link that is embeded in the hint. 
After opening the link that was given in the hint. I saw how the browser and version will look like so now i had filtered the packets with only ```HTTP Request's``` . Then i start analysing. and saw one request where all the browser and it's version was written.

    ![promisechains](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/FORENSICS/Level1-final.png?raw=true "Follow TCP Stream")
   
   So now read question again. The flag is "BrowserName BrowserVersion" and we need to write the version in 3 decimal value only suppose the version is ```1.2.3.4``` then type ```1.2.3``` only.  
   
4. So the browser name and it's version is : ```Chrome/40.0.2214.93```
   ```bash
   So the flag is: Chrome 40.0.2214
   ```
   Thanks :) 
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

