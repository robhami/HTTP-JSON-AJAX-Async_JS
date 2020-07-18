## AJAX ##
Allows you to read from webserver after the page has loaded and update webpage without reloading it.

### XML HTTP request ###
Achieved using a tool that browsers built called: XML HTTP request. Old way.
```
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
       // Typical action to be performed when the document is ready:
       document.getElementById("demo").innerHTML = xhttp.responseText;
    }
};
xhttp.open("GET", "filename", true);
xhttp.send();
```

### JQuery ###
New Old way: JQuery.

``` 
$.getJSON('my/url', function(data) {

});
```

### Fetch ###
Current way.

```
fetch('/my/url').then(response => {
  console.log(response);
});

```

This updating allows single page application - a trend with web apps.

Fetch is a function in the window. Can do the below in console: 

```
>fetch('https://jsonplaceholder.typicode.com/users');


<Promise {<pending>}
__proto__: Promise
[[PromiseStatus]]: "resolved"
[[PromiseValue]]: Response
body: (...)
bodyUsed: false
headers: Headers {}
ok: true
redirected: false
status: 200
statusText: ""
type: "cors"
url: "https://jsonplaceholder.typicode.com/users"
__proto__: Response

```

Promise is making a request to location on internet, it will let you know when I have the value. To access promises you do: 

.then

```

fetch('https://jsonplaceholder.typicode.com/users').then(response => console.log(response));
Promise {<pending>}
VM108:1 
Response {type: "cors", url: "https://jsonplaceholder.typicode.com/users", redirected: false, status: 200, ok: true, …}
body: ReadableStream
bodyUsed: false
headers: Headers {}
ok: true
redirected: false
status: 200
statusText: ""
type: "cors"
url: "https://jsonplaceholder.typicode.com/users"
__proto__: Response

```
fetch comes with its own method called .json()

```
>fetch('https://jsonplaceholder.typicode.com/users').then(response=>response.json());
<Promise {<pending>}
__proto__: Promise
[[PromiseStatus]]: "resolved"
[[PromiseValue]]: Array(10)
0: {id: 1, name: "Leanne Graham", username: "Bret", email: "Sincere@april.biz", address: {…}, …}
1: {id: 2, name: "Ervin Howell", username: "Antonette", email: "Shanna@melissa.tv", address: {…}, …}
2: {id: 3, name: "Clementine Bauch", username: "Samantha", email: "Nathan@yesenia.net", address: {…}, …}
3: {id: 4, name: "Patricia Lebsack", username: "Karianne", email: "Julianne.OConner@kory.org", address: {…}, …}
4: {id: 5, name: "Chelsey Dietrich", username: "Kamren", email: "Lucio_Hettinger@annie.ca", address: {…}, …}
5: {id: 6, name: "Mrs. Dennis Schulist", username: "Leopoldo_Corkery", email: "Karley_Dach@jasper.info", address: {…}, …}
6: {id: 7, name: "Kurtis Weissnat", username: "Elwyn.Skiles", email: "Telly.Hoeger@billy.biz", address: {…}, …}
7: {id: 8, name: "Nicholas Runolfsdottir V", username: "Maxime_Nienow", email: "Sherwood@rosamond.me", address: {…}, …}
8: {id: 9, name: "Glenna Reichert", username: "Delphine", email: "Chaim_McDermott@dana.io", address: {…}, …}
9: {id: 10, name: "Clementina DuBuque", username: "Moriah.Stanton", email: "Rey.Padberg@karina.biz", address: {…}, …}
length: 10
__proto__: Array(0)

```
if add then again with parameter data- it will just pull the data:

```
fetch('https://jsonplaceholder.typicode.com/users').then(response=>response.json().then(data=>console.log(data)));
Promise {<pending>}
VM261:1 (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```

This is same if Robofriends app: 
```
fetch ('https://jsonplaceholder.typicode.com/users')
        .then (response => {
          return response.json();
        })
        .then(users => {
          this.setState({users: users});
          
      });
```
Can add JSONview add on to Chrome to make it more readable. 
