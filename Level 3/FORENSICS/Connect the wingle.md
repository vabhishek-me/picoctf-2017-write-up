# Connect The Wigle
---
### Question
Identify the data contained within wigle and determine how to visualize it. Update 16:26 EST 1 Apr If you feel that you are close, make a private piazza post with what you have, and an admin will help out.

### HINTS

Perhaps they've been storing data in a database. How do we access the information?
How can we visualize this data? Maybe we just need to take a step back to get the big picture?
Try zero in the first word of the flag, if you think it's an O.
If you think you're super close, make a private piazza post with what you think it is.

---
# Solution

It was pitty simple challenge. We got one file:

```
wigle
```
1. First thing i had done was to check the filetype. I quickly typed:
    ```bash
    $file wigle 
    wigle: SQLite 3.x database
    ```

2. So, it reveals that it is ``` SQLite 3.x database``` database file. 
3. So if you remember my Writeup on Biscuit Challenge then their i gave [link](./Level%203/WEB-EXPLOITATION/Biscuit.md) to read(Just read it...). Then i opened in in sqlite3:
    ```bash
    sqlite3 wigle
    SQLite version 3.8.2 2013-12-06 14:53:30
    Enter ".help" for instructions
    Enter SQL statements terminated with a ";"
    sqlite> 
    ```

4. Now lets dump the tables:
    ```bash
    sqlite>select * from sqlite_master where type='table';
    table|android_metadata|android_metadata|2|CREATE TABLE android_metadata (locale text)
    table|location|location|3|CREATE TABLE location (_id int, bssid text, level int, lat double, lon double, altitude double, accuracy float, time long)
    table|network|network|4|CREATE TABLE network (bssid text, ssid text, frequency int, capabilities text, lasttime long, lastlat double, lastlon double, type text)
    ```

5. So we got the tables. The table location seems intresting so lets dump it.
    ```bash
    sqlite> select * from location;
    0|3a:13:4d:05:ee:15|-75|-20.0|-5.96|144.0|12.0|1490962260
    1|be:b5:e8:3f:d3:87|-82|-19.99|-5.96|135.0|8.0|1490952148
    2|a8:ba:ae:5a:70:77|-95|-19.98|-5.96|132.0|16.0|1490966402
    3|bb:67:49:e9:66:06|-74|-19.98|-5.955|151.0|6.0|1490952729
    4|07:b9:09:e4:64:51|-75|-19.98|-5.95|142.0|12.0|1490968425
    5|a0:33:2d:80:fe:dc|-78|-19.97|-5.96|146.0|16.0|1490957848
    6|f1:63:d5:7a:8d:e2|-90|-19.96|-5.96|134.0|8.0|1490953918
    7|74:bb:d6:5b:b2:46|-79|-19.96|-5.95|148.0|12.0|1490953906
    8|90:e2:d1:e0:c3:7f|-85|-19.96|-5.94|131.0|12.0|1490954545
    9|28:2e:86:ff:7e:94|-80|-20.0|-5.86|145.0|4.0|1490955561
    10|67:91:ba:a2:17:49|-85|-19.99|-5.86|132.0|16.0|1490955288
    11|2a:7c:91:a7:ab:f6|-73|-19.98|-5.86|147.0|16.0|1490952970
    12|e3:02:8d:5e:1f:f6|-80|-19.97|-5.86|137.0|8.0|1490958003
    13|05:67:e4:6e:cf:41|-91|-19.96|-5.86|133.0|4.0|1490963623
    14|af:9e:25:51:40:3c|-88|-19.95|-5.86|138.0|12.0|1490968508
    15|e7:70:23:f1:cc:ed|-78|-20.0|-5.84|135.0|12.0|1490962247
    16|60:f7:32:6b:67:e0|-72|-20.0|-5.85|151.0|4.0|1490958823
    17|bc:56:40:c5:08:7b|-85|-19.99|-5.76|138.0|12.0|1490955148
    18|95:56:32:28:94:55|-73|-20.0|-5.76|136.0|8.0|1490956318
    19|1b:c5:fc:18:f5:c5|-74|-20.0|-5.74|132.0|8.0|1490952913
    20|ad:21:48:38:97:14|-77|-19.99|-5.74|146.0|12.0|1490966098
    21|db:ac:de:fe:b2:de|-88|-19.98|-5.74|131.0|12.0|1490965264
    22|13:ee:90:fb:00:9b|-81|-19.98|-5.76|130.0|6.0|1490967402
    23|a2:3c:7f:f6:ce:cd|-79|-19.96|-5.74|144.0|4.0|1490959414
    24|74:5c:e4:77:4d:4a|-86|-19.95|-5.745|150.0|8.0|1490963213
    25|ab:7a:93:d2:36:be|-95|-19.95|-5.755|132.0|4.0|1490956488
    26|2a:18:ec:83:92:ff|-78|-19.96|-5.76|140.0|8.0|1490953990
    27|fb:e8:42:45:ce:1f|-74|-19.98|-5.75|144.0|6.0|1490964389
    28|86:c0:ee:ab:cb:1f|-84|-19.97|-5.76|151.0|12.0|1490956055
    29|45:31:82:a4:2f:f2|-72|-19.97|-5.74|133.0|8.0|1490964632
    30|ce:17:ae:b7:a3:c5|-71|-19.99|-5.66|142.0|6.0|1490967879
    --more--
    ```
6. Too many data lets take location as latitude and longitude. Lets dump only lat and lon
    ```bash
    sqlite> select lat, lon from location;
    -20.0|-5.96
    -19.99|-5.96
    -19.98|-5.96
    -19.98|-5.955
    -19.98|-5.95
    -19.97|-5.96
    -19.96|-5.96
    -19.96|-5.95
    -19.96|-5.94
    -20.0|-5.86
    -19.99|-5.86
    -19.98|-5.86
    -19.97|-5.86
    -19.96|-5.86
    -19.95|-5.86
    -20.0|-5.84
    -20.0|-5.85
    -19.99|-5.76
    -20.0|-5.76
    -20.0|-5.74
    -19.99|-5.74
    -19.98|-5.74
    -19.98|-5.76
    -19.96|-5.74
    -19.95|-5.745
    --more--
   ```

    Now lets put it in a file name ```cordinates.txt``` > ```Save it``` and if you know bash then it will be easy for you. you can use sed command for replacing ```|``` to comma: ```,``` . 

   ```bash
    $sed -i 's/|/,/g' cordinates.txt
    $cat cordinates.txt | more
    -20.0,-5.96
    -19.99,-5.96
    -19.98,-5.96
    -19.98,-5.955
    -19.98,-5.95
    -19.97,-5.96
    -19.96,-5.96
    -19.96,-5.95
    -19.96,-5.94
    -20.0,-5.86
    -19.99,-5.86
    -19.98,-5.86
    -19.97,-5.86
    -19.96,-5.86
    -19.95,-5.86
    -20.0,-5.84
    -20.0,-5.85
    -19.99,-5.76
    -20.0,-5.76
    -20.0,-5.74
    -19.99,-5.74
    -19.98,-5.74
    -19.98,-5.76
    -19.96,-5.74
    -19.95,-5.745
    -19.95,-5.755
    -19.96,-5.76
    -19.98,-5.75
    -19.97,-5.76
    -19.97,-5.74
    -19.99,-5.66
    -20.0,-5.655
    -20.0,-5.645
    -19.99,-5.64
    -19.98,-5.64
    -19.98,-5.66
    --More--
   ```

    Now just give these cordinates in any Lat/Long pointing tool, I am going to use [this](https://www.darrinward.com/). Just give cordinates.and you will be able to 
    
    ![](./flag.png)

     So, i think we got the flag 
     ```
     FLAG{f0und_m3_EE263B5F}
     ```
     
     Hope you liked it :)
     
   ~Thanks
   
    [@spiritedwolf](https://github.com/spiritedwolf)

---

