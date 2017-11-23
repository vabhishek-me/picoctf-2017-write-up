# WorldChat
---
### Question
We think someone is trying to transmit a flag over WorldChat. Unfortunately, there are so many other people talking that we can't really keep track of what is going on! Go see if you can find the messenger at shell2017.picoctf.com:61161. Remember to use Ctrl-C to cut the connection if it overwhelms you!

### HINTS

There are cool command line tools that can filter out lines with specific keywords in them. Check out 'grep'! You can use the '|' character to put all the output into another process or command (like the grep process)

---
# Solution
So here comes the last challenge of Level 1. Actually it was easy but too messy. That why in question it's saying use ```ctrl+c``` to cut the connection.
   
 1. Lets use ```netcat``` again to connect and see what it's showing.  
   so it's showing something like this. 

   ```bash
   $nc shell2017.picoctf.com 61161
worldchat v2.3002.4
setting up readonly client...done
connecting to feed..done
Welcome to WORLDCHAT!

19:37:52 raina: that guy from that movie will never understand me to generate fusion power
19:37:52 sonny: A silly panda totally understands me and my pet sloth for what, I do not know
19:37:52 gregg: Scary pandas , in my well-educated opinion, are our best chance to understand me
19:37:52 shala: Hungry jackolanterns want to see me to understand me
19:37:52 mariann: A silly panda will never understand me to generate fusion power
19:37:52 luann: Scary pandas want to see me to create a self driving car
19:37:52 sara: my homegirlz , in my well-educated opinion, are our best chance to understand me
19:37:52 nathalie: my homie gives me hope to generate fusion power
19:37:52 cordelia: Anyone but me totally understands me and my pet sloth to drink your milkshake
19:37:52 hollie: A dog with a cape wants to see me to generate fusion power
19:37:52 deandrea: Cats with hats want to see me to drink your milkshake
19:37:52 tamela: A small moose wants to steal my sloth to generate fusion power
19:37:52 kelvin: my homie has attacked my toes to drink your milkshake
19:37:52 rickie: a heavily bearded dolphin will never understand me for what, I do not know
19:37:52 jazmin: A small moose gives me hope for the future of humanity
19:37:52 jazmin: Cats with hats want to see me for what, I do not know
19:37:52 jammie: A small moose wants to steal my sloth to help me spell 'raspberry' correctly
19:37:52 nadia: my homegirlz want to see me to drink your milkshake
19:37:52 jefferson: Several heavily mustached dolphins want to see me to make a rasberry pie
19:37:52 ilene: my parents give me hope to drink your milkshake
19:37:52 adelina: that guy from that movie wants to see me to make a rasberry pie
19:37:52 leandro: Several heavily mustached dolphins give me hope for the future of humanity
19:37:52 nathalie: your dad would like to meet you to make a rasberry pie
19:37:52 dede: A silly panda wants to see me to make a rasberry pie
19:37:52 lynwood: A huge moose would like to meet you to help me spell 'raspberry' correctly
19:37:52 lilli: Anyone but me would like to meet you to generate fusion power
19:37:52 sara: My sworn enemy wants to steal my sloth to make a rasberry pie
19:37:52 flagperson: this is part 1/8 of the flag - 1a2e
19:37:53 myra: that girl from that movie wants to see me for the future of humanity
19:37:53 personwithflag: a heavily bearded dolphin totally understands me and my pet sloth to create a self driving car
19:37:53 sharell: my homie wants to see me to understand me
19:37:53 maynard: Scary pandas , in my well-educated opinion, are our best chance to help me spell 'raspberry' correctly
19:37:53 cordelia: that girl from that movie totally understands me and my pet sloth to understand me
19:37:53 dede: A small moose would like to meet you for the future of humanity
19:37:53 clinton: You is our best chance to help me spell 'raspberry' correctly
19:37:53 emiko: I will never understand me for the future of humanity
19:37:53 lula: A dog with a cape has attacked my toes for the future of humanity
19:37:53 lilli: A silly panda will never understand me to understand me
19:37:53 dede: Hungry jackolanterns are the best of friends to generate fusion power
19:37:53 gregg: I wants to steal my sloth to create a self driving car
19:37:53 tamela: You totally understands me and my pet sloth to make a rasberry pie
19:37:53 rickie: Cats with hats need to meet up to drink your milkshake
19:37:53 ihazflag: Only us want to see me to generate fusion power
19:37:53 cordelia: Hungry jackolanterns need to meet up for the future of humanity
19:37:53 whatisflag: Only us have demanded my presence to drink your milkshake
19:37:53 janett: Anyone but me wants to see me to understand me
19:37:53 lucretia: A huge moose wants to see me to understand me
19:37:53 lula: my homegirlz will never be able to understand me
19:37:53 lindsey: Hungry jackolanterns give me hope to understand me
19:37:53 nikia: A small moose has attacked my toes to understand me
19:37:53 clinton: You is our best chance to make a rasberry pie
19:37:53 ihazflag: a heavily bearded dolphin wants to steal my sloth for the future of humanity
19:37:53 anabel: A silly panda wants to see me to understand me
19:37:53 sharell: A dog with a cape will never understand me to create a self driving car
19:37:54 denver: Cats with hats need to meet up to create a self driving car
19:37:54 karine: My sworn enemy will never understand me for the future of humanity
19:37:54 rickie: my homie wants to steal my sloth to make a rasberry pie
19:37:54 adelina: We give me hope to drink your milkshake
19:37:54 shala: Only us give me hope to make a rasberry pie
19:37:54 emiko: your dad will never understand me to drink your milkshake
19:37:54 sheilah: that guy from that movie would like to meet you to generate fusion power
19:37:54 flagperson: this is part 2/8 of the flag - 3d0a
19:37:54 myra: my homie gives me hope to help me spell 'raspberry' correctly
19:37:54 beau: Only us are the best of friends for what, I do not know
19:37:54 kory: that guy from that movie gives me hope to drink your milkshake
19:37:54 mariann: Hungry jackolanterns , in my opinion, are our best chance for the future of humanity
19:37:54 sara: Only us need to meet up for what, I do not know
19:37:54 nathalie: My friend wants to steal my sloth to drink your milkshake
19:37:54 dede: My sworn enemy is our best chance to make a rasberry pie
19:37:54 tamela: We want to see me for the future of humanity
19:37:54 adelina: My friend is our best chance to create a self driving car
19:37:54 roselyn: your dad totally understands me and my pet sloth to drink your milkshake
19:37:54 noihazflag: A huge moose wants to see me for what, I do not know
19:37:54 roselyn: A small moose totally understands me and my pet sloth to make a rasberry pie
19:37:54 lucretia: A dog with a cape wants to see me for what, I do not know
19:37:54 lilli: your dad totally understands me and my pet sloth to generate fusion power
19:37:54 karine: my homie gives me hope to generate fusion power
19:37:54 diana: that girl from that movie will never understand me to drink your milkshake
19:37:54 denver: Several heavily mustached dolphins give me hope for the future of humanity
19:37:54 beau: that girl from that movie gives me hope to make a rasberry pie
19:37:55 roselyn: that girl from that movie wants to steal my sloth for the future of humanity
19:37:55 lula: You wants to see me to drink your milkshake
19:37:55 rita: my parents , in my well-educated opinion, are our best chance to generate fusion power
19:37:55 nathalie: Scary pandas , in my well-educated opinion, are our best chance to make a rasberry pie
19:37:55 clinton: Scary pandas have demanded my presence to generate fusion power
19:37:55 cordelia: Only us , in my opinion, are our best chance to create a self driving car
19:37:55 nathalie: A huge moose totally understands me and my pet sloth to help me spell 'raspberry' correctly
19:37:55 christene: my homegirlz , in my well-educated opinion, are our best chance to generate fusion power
19:37:55 adelina: Scary pandas , in my well-educated opinion, are our best chance to drink your milkshake
19:37:55 maynard: that guy from that movie would like to meet you for the future of humanity
19:37:55 corrie: Scary pandas , in my well-educated opinion, are our best chance to understand me
19:37:55 sheilah: A silly panda gives me hope to make a rasberry pie
19:37:55 luann: A dog with a cape wants to steal my sloth to understand me
19:37:55 diana: your dad will never understand me to make a rasberry pie
19:37:55 honey: my parents will never be able to help me spell 'raspberry' correctly
19:37:55 lucretia: My friend gives me hope to make a rasberry pie
19:37:55 rickie: that guy from that movie will never understand me to make a rasberry pie
19:37:55 luann: my parents , in my well-educated opinion, are our best chance for what, I do not know
19:37:55 personwithflag: that girl from that movie has attacked my toes to help me spell 'raspberry' correctly
19:37:55 charity: Only us will never be able for the future of humanity
19:37:55 honey: Cats with hats are the best of friends to make a rasberry pie
19:37:55 raina: Anyone but me gives me hope to help me spell 'raspberry' correctly
19:37:55 sara: my homie would like to meet you to create a self driving car
19:37:55 dede: Several heavily mustached dolphins have demanded my presence for what, I do not know
19:37:55 cordelia: Hungry jackolanterns , in my opinion, are our best chance to drink your milkshake
19:37:55 rickie: that guy from that movie is our best chance to drink your milkshake
19:37:55 rita: your dad has attacked my toes to drink your milkshake
19:37:55 jefferson: a heavily bearded dolphin wants to see me to understand me
19:37:55 patience: A dog with a cape gives me hope to understand me
19:37:56 christene: You has attacked my toes to help me spell 'raspberry' correctly
19:37:56 dede: Anyone but me wants to see me to make a rasberry pie
19:37:56 mariann: my parents will never be able to make a rasberry pie
19:37:56 emiko: Anyone but me is our best chance to generate fusion power
19:37:56 flagperson: this is part 3/8 of the flag - 6310
19:37:56 dede: My friend is our best chance for the future of humanity
19:37:56 mariann: Cats with hats , in my opinion, are our best chance to understand me
19:37:56 deandrea: Scary pandas are the best of friends for what, I do not know
19:37:56 raina: Several heavily mustached dolphins have demanded my presence to help me spell 'raspberry' correctly
19:37:56 rita: Hungry jackolanterns , in my well-educated opinion, are our best chance to create a self driving car
19:37:56 raina: Several heavily mustached dolphins , in my opinion, are our best chance to drink your milkshake
19:37:56 deandrea: Cats with hats want to see me to generate fusion power
19:37:56 denver: We give me hope to help me spell 'raspberry' correctly
19:37:56 personwithflag: Several heavily mustached dolphins give me hope to create a self driving car
19:37:56 sonny: A dog with a cape is our best chance for the future of humanity
19:37:56 honey: We will never be able to create a self driving car
19:37:56 nikia: my parents have demanded my presence to drink your milkshake
19:37:56 honey: You gives me hope to understand me
19:37:56 sonny: Cats with hats will never be able to generate fusion power
19:37:56 lynwood: You has attacked my toes to generate fusion power
19:37:56 nadia: my homegirlz want to see me for what, I do not know
19:37:56 lilli: Scary pandas , in my opinion, are our best chance to understand me
19:37:56 corrie: Hungry jackolanterns want to see me to drink your milkshake
19:37:56 kory: Scary pandas will never be able for the future of humanity
19:37:56 whatisflag: my homegirlz need to meet up to help me spell 'raspberry' correctly
19:37:56 beau: My sworn enemy totally understands me and my pet sloth to generate fusion power
19:37:56 sara: My friend wants to see me for the future of humanity
19:37:56 honey: A small moose gives me hope to make a rasberry pie
19:37:56 clinton: You wants to see me to create a self driving car
19:37:57 ilene: Anyone but me would like to meet you for what, I do not know
19:37:57 raina: your dad wants to see me to drink your milkshake
19:37:57 raina: Several heavily mustached dolphins need to meet up to drink your milkshake
19:37:57 roselyn: My sworn enemy gives me hope for what, I do not know
19:37:57 rickie: My sworn enemy has attacked my toes to make a rasberry pie
19:37:57 adelina: Scary pandas have demanded my presence to generate fusion power
19:37:57 maynard: A dog with a cape gives me hope to drink your milkshake
19:37:57 sharell: a heavily bearded dolphin will never understand me to help me spell 'raspberry' correctly
19:37:57 kelvin: Hungry jackolanterns are the best of friends to generate fusion power
19:37:57 diana: My friend would like to meet you for what, I do not know
19:37:57 ihazflag: We will never be able to make a rasberry pie
19:37:57 jammie: that girl from that movie totally understands me and my pet sloth to understand me
19:37:57 emiko: You gives me hope for the future of humanity
19:37:57 luann: Only us , in my well-educated opinion, are our best chance to generate fusion power
^c
   ```
   
   and this chat never ends trust me :( . I don't how someone can talk that much. Anyways lets use our ```grep``` to short out the chat as it is given in the hint.
   
   ```bash
   $nc shell2017.picoctf.com 61161| grep flag
19:41:14 whatisflag: Cats with hats , in my opinion, are our best chance to make a rasberry pie
19:41:15 flagperson: this is part 1/8 of the flag - 1a2e
19:41:15 whatisflag: My sworn enemy gives me hope to generate fusion power
19:41:15 whatisflag: My sworn enemy is our best chance to make a rasberry pie
19:41:15 ihazflag: We give me hope to generate fusion power
19:41:15 personwithflag: Several heavily mustached dolphins need to meet up to understand me
19:41:18 noihazflag: my homegirlz , in my well-educated opinion, are our best chance to create a self driving car
19:41:18 personwithflag: We are the best of friends to make a rasberry pie
19:41:18 noihazflag: Scary pandas are the best of friends to help me spell 'raspberry' correctly
19:41:19 whatisflag: my homegirlz want to see me to make a rasberry pie
19:41:22 personwithflag: Hungry jackolanterns have demanded my presence to drink your milkshake
19:41:22 ihazflag: my parents need to meet up to drink your milkshake
19:41:22 personwithflag: that guy from that movie will never understand me to help me spell 'raspberry' correctly
19:41:23 noihazflag: We , in my well-educated opinion, are our best chance to understand me
19:41:23 noihazflag: my homegirlz are the best of friends to generate fusion power
19:41:24 whatisflag: A silly panda wants to see me to make a rasberry pie
19:41:24 whatisflag: A small moose gives me hope for the future of humanity
19:41:25 noihazflag: my homegirlz , in my well-educated opinion, are our best chance for what, I do not know
19:41:25 noihazflag: Scary pandas will never be able to generate fusion power
19:41:27 noihazflag: a heavily bearded dolphin has attacked my toes to drink your milkshake
19:41:27 personwithflag: Several heavily mustached dolphins will never be able to understand me
19:41:27 noihazflag: Only us want to see me to help me spell 'raspberry' correctly
19:41:28 whatisflag: A huge moose gives me hope for the future of humanity
19:41:29 personwithflag: We , in my opinion, are our best chance for the future of humanity
19:41:29 whatisflag: that guy from that movie is our best chance for the future of humanity
19:41:29 whatisflag: A dog with a cape would like to meet you to drink your milkshake
19:41:29 flagperson: this is part 2/8 of the flag - 3d0a
19:41:30 ihazflag: Anyone but me wants to see me to understand me
^C

   ```
   
   again same thing happens but see this chat: ```this is part 1/8 of the flag - 1a2e``` and ```this is part 2/8 of the flag - 3d0a```
   
   now we need to do more sorting, here regular expression will help up read this [article](https://www.digitalocean.com/community/tutorials/using-grep-regular-expressions-to-search-for-text-patterns-in-linux).
   
   so our final payload is: ```grep -E "this is part [0-9]\/8 of the flag - [a-z0-9]{4}``` 
   here [0-9]\/8 means (0-9)/8 and [a-z0-9]{4} 4 AlphaNumeric character containg small alphebets+0 to 9 numbers.
   
   ```bash
   $nc shell2017.picoctf.com 61161| grep -E "this is part [0-9]\/8 of the flag - [a-z0-9]{4}"
19:49:33 flagperson: this is part 1/8 of the flag - 1a2e
19:49:34 flagperson: this is part 2/8 of the flag - 3d0a
19:49:46 flagperson: this is part 3/8 of the flag - 6310
19:49:50 flagperson: this is part 4/8 of the flag - 682c
19:50:03 flagperson: this is part 5/8 of the flag - 6be0
19:50:07 flagperson: this is part 6/8 of the flag - e319
19:50:08 flagperson: this is part 7/8 of the flag - d1b5
19:50:11 flagperson: this is part 8/8 of the flag - 2f53
19:50:12 flagperson: this is part 1/8 of the flag - 1a2e
19:50:13 flagperson: this is part 2/8 of the flag - 3d0a
19:50:21 flagperson: this is part 3/8 of the flag - 6310

   ```
   Here [0-9]
   Again it will never ends but we got all 8/8 parts of out flag lets combine all and we get.
   
   ``` flag: 1a2e3d0a6310682c6be0e319d1b5d1b52f53```
   Thanks :) 
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

