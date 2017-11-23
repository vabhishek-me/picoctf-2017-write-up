# Lazy Dev
---
### Question
I really need to login to this website, but the developer hasn't implemented [login](http://shell2017.picoctf.com:43393/) yet. Can you help?

### HINTS

Where does the password check actually occur?
Can you interact with the javascript directly?

---
# Solution
So we have done all challenges in Level one now just master challenge left to move into the next level. This challenge was super easy it was just based on JS. Lets do it

1. So we opened the [website](http://shell2017.picoctf.com:43393/) and we saw
 ![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/Master/first.png?raw=true)

   See in the inspect elements and read that ```static/client.js``` file.
   ```JS
    //Validate the password. TBD!
    function validate(pword){
      //TODO: Implement me
      return false;
    }
    
    //Make an ajax request to the server
    function make_ajax_req(input){
      var text_response;
      var http_req = new XMLHttpRequest();
      var params = "pword_valid=" + input.toString();
      http_req.open("POST", "login", true);
      http_req.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
      http_req.onreadystatechange = function() {//Call a function when the state changes.
      	if(http_req.readyState == 4 && http_req.status == 200) {
          document.getElementById("res").innerHTML = http_req.responseText;
        }
      }
      http_req.send(params);
    }
    
    //Called when the user submits the password
    function process_password(){
      var pword = document.getElementById("password").value;
      var res = validate(pword);
      var server_res = make_ajax_req(res);
    }       
   ```
   
   read the starting code:- 
   
   ```JS
   //Validate the password. TBD!
    function validate(pword){
      //TODO: Implement me
      return false;
    }
   ```
   
   So, it's returning ```false```. What if we change it xD to ```true```.
   
   Lets do it. I am gonna use [BurpSuite](https://www.youtube.com/watch?v=8fO9pcSL4IM).
   
   ![](https://github.com/iammrdollar/picoctf-2017-write-up/blob/master/Level%201/Master/master1-main.png?raw=true)
   
   and after changing  ```false``` to ```true``` forward the request. And wola! you got the flag ;) 
   
   ```
   Flag:client_side_is_the_dark_sidea99c64effed2c2f1c9347eff536e949c
   ```
   Thanks :) 
   
   [@spiritedwolf](https://github.com/spiritedwolf)

---

