## JSON ##

Can only send text from browser to server.

JSON: Javascript Object Notation. 

JSON is a syntax for storing and exchanging data. XML is another way. JSON is used more now and is better.

JSON is text, written with Javascript object notation.


JSON is a little bit different from Javascript: 

It uses double quotes ("). Everything has to be a string with double quotes.
```
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  }
  
  ]
  
  ```
  
  JSON can be read by any language.
  
  ### JSON.parse () ###
  
  Converts JSON data to an object:
  
  ```
  var obj = JSON.parse('{"name":"John","age":30,"city":"New York"}');
  ```
 
  ### JSON.stringify() ### 
  
  Converts an object to JSON data: 
  ```
  var myJSON = JSON.stringify(obj)
  ```
  This can now be put into HTTP request.
  
  ### Misc ###
  NB can also submit JSON from an "<input>".
  
