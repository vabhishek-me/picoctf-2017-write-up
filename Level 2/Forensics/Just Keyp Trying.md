# Just Keyp Trying
---
### Question
Here's an interesting capture of some data. But what exactly is this data? Take a look: data.pcap

### HINTS

Find out what kind of packets these are. What does the info column say in Wireshark/Cloudshark?
What changes between packets? What does that data look like?
Maybe take a look at http://www.usb.org/developers/hidpage/Hut1_12v2.pdf?

---
# Solution
It was amazing challenge. Everything you need to do is just follow the hint. 
##### Q1. Find out what kind of packets these are. What does the info column say in Wireshark/Cloudshark?

##### Q2. What changes between packets? What does that data look like?

##### Q3. Maybe take a look at http://www.usb.org/developers/hidpage/Hut1_12v2.pdf?

So, lets try to find out the answers.
![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%202/Forensics/data-pcap-in-wireshark.png?raw=true)
##### Answer1:- We came to know these are the usb packets. 

##### Answer2:- Read this [Article](https://osqa-ask.wireshark.org/questions/11054/analysing-usb-traffic).

##### Answer3:- just read it.

So i simply opened this ```data.pcap``` file with tshark

 ```bash
  $tshark -r data.pcap -V | more
  Frame 1: 35 bytes on wire (280 bits), 35 bytes captured (280 bits)
    Encapsulation type: USB packets with USBPcap header (153)
    Arrival Time: Mar 23, 2017 06:37:16.777061000 IST
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1490231236.777061000 seconds
    [Time delta from previous captured frame: 0.000000000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 0.000000000 seconds]
    Frame Number: 1
    Frame Length: 35 bytes (280 bits)
    Capture Length: 35 bytes (280 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: usb]
USB URB
    USBPcap pseudoheader length: 27
    IRP ID: 0xffffb689ac2d3940
    IRP USBD_STATUS: USBD_STATUS_SUCCESS (0x00000000)
    URB Function: URB_FUNCTION_BULK_OR_INTERRUPT_TRANSFER (0x0009)
    IRP information: 0x01, Direction: PDO -> FDO
        0000 000. = Reserved: 0x00
        .... ...1 = Direction: PDO -> FDO (0x01)
    URB bus id: 2
    Device address: 1
    Endpoint: 0x81, Direction: IN
        1... .... = Direction: IN (1)
        .000 0001 = Endpoint value: 1
    URB transfer type: URB_INTERRUPT (0x01)
    Packet Data Length: 8
    [bInterfaceClass: Unknown (0xffff)]
Leftover Capture Data: 0000090000000000

Frame 2: 35 bytes on wire (280 bits), 35 bytes captured (280 bits)
    Encapsulation type: USB packets with USBPcap header (153)
    Arrival Time: Mar 23, 2017 06:37:16.914192000 IST
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1490231236.914192000 seconds
    [Time delta from previous captured frame: 0.137131000 seconds]
--More--
  ```
  
  So notice the ```Leftover Capture Data``` just grep all the Leftover Capture Data using 
  ```bash
  grep "Leftover Capture Data"
  ```
  
  so lets do it,
  ```bash
  tshark -r data.pcap -V | grep "Leftover Capture Data"
Leftover Capture Data: 0000090000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 00000f0000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000040000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 00000a0000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 20002f0000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000130000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000150000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000200000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000220000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000220000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 20002d0000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000270000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000110000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 00001a0000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000040000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000150000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000070000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000160000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 20002d0000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000050000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000250000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000210000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000250000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000220000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000070000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000220000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0000090000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 2000300000000000
Leftover Capture Data: 2000000000000000
Leftover Capture Data: 0000000000000000
Leftover Capture Data: 0100000000000000
Leftover Capture Data: 0100060000000000
  ```
  
  now lets read that pdf
  
  so we tried to decode the cipher 
  ```bash
  tshark -r data.pcap -V | grep "Leftover Capture Data"
Leftover Capture Data: 0000090000000000-->f and F
Leftover Capture Data: 00000f0000000000-->l and L
Leftover Capture Data: 0000040000000000-->a and A
Leftover Capture Data: 00000a0000000000-->g and G
Leftover Capture Data: 20002f0000000000-->[ and {
Leftover Capture Data: 0000130000000000-->p and P
Leftover Capture Data: 0000150000000000-->r and R
Leftover Capture Data: 0000200000000000-->3 and #
Leftover Capture Data: 0000220000000000-->5 and %
Leftover Capture Data: 0000220000000000-->5 and %
Leftover Capture Data: 20002d0000000000-->- and _
Leftover Capture Data: 0000270000000000-->0 and )
Leftover Capture Data: 0000110000000000-->n and N
Leftover Capture Data: 00001a0000000000-->w and W
Leftover Capture Data: 0000040000000000-->a and A
Leftover Capture Data: 0000150000000000-->r and R
Leftover Capture Data: 0000070000000000-->d and D
Leftover Capture Data: 0000160000000000-->s and S
Leftover Capture Data: 20002d0000000000-->- and _
Leftover Capture Data: 0000050000000000-->b and B
Leftover Capture Data: 0000250000000000-->8 and *
Leftover Capture Data: 0000210000000000-->4 and $
Leftover Capture Data: 0000250000000000-->8 and *
Leftover Capture Data: 0000220000000000-->5 and %
Leftover Capture Data: 0000070000000000-->d and D
Leftover Capture Data: 0000220000000000-->5 and %
Leftover Capture Data: 0000090000000000-->f and F
Leftover Capture Data: 2000300000000000-->] and }
Leftover Capture Data: 0100060000000000-->c and C
  ```
  Now just write down th flag:-
  ```
  flag{pr335_0nwards_b8485d5f}
  ```
  
  Hope you liked it
   ~Thanks
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

