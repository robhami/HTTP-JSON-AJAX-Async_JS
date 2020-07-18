## Promises ##

New in ES6. 

A promise is an object that may produce a single value some time in the future. 
Either a resolved value, or a reason that it;s not resolved (rejected). 

3 possible states of promises: 

1. Fullfilled
2. Pending
3. Rejected

Before promises we used callbacks: 

Have element with eventlistener that when user clicks we are going to have the callback submitForm
```
el.addEventListener("click", submitForm);
```
Also each function below is a callback: 
```
movePlayer(100, "left", function () {
  movePlayer(400, "left", function () {
    movePlayer(10, "right", function () {
      movePlayer(330, "left", function () {
      });
    });
  });
});

```
The above is nested and complex to read. Promises look like this:

```
movePlayer(100,'Left')
  .then(() => movePlayer(400, 'Left'))
   .then(() => movePlayer(10, 'Right'))
     .then(() => movePlayer(330, 'Left'))
```
### Create Promise ###
To create a promise (add below to console): 
```
const promise = new Promise ((resolve, reject) => {
	if (true) {
		resolve("Stuff worked");
	} else {
		reject("Error, it broke")
	}
})
```
Then run the promise and make it true?how?by making if = true:

```
promise.then(result => console.log(result));
```
### Chain Promises ###
Can chain then's to add ! mark: 

```
>promise
	.then(result=> result + '!')
	.then(result2 => console.log(result2));
<VM122:3 Stuff worked!
```

### catch error method ###
Can use .catch method to catch errors (need curly brackets around result2 function): 
```
promise
	.then(result=> result + '!')

	.then(result2 => {
		throw Error
		console.log(result2);
		})
	.catch(() => console.log("error!"))
VM152:8 error!
Promise {<resolved>: undefined}
```

Without error: 

```
promise
	.then(result=> result + '!')
	.then(result2 => result2 + '?')
	.catch(() => console.log("error!"))
	.then(result3=>{
		// throw Error
		console.log(result3+'!');
	})
VM93:7 Stuff worked!?!
Promise {<resolved>: undefined}
```
If add error below catch, it will not run: 

```
promise
	.then(result=> result + '!')
	.then(result2 => result2 + '?')
	.catch(() => console.log("error!"))
	.then(result3=>{
		throw Error
		console.log(result3+'!');
	})
Promise {<rejected>: ƒ}
users:1 Uncaught (in promise) ƒ Error() { [native code] }
```

So need to put catch at end, as only checks before .catch statment. 

### Promise all ###
Promise.all() - takes an array of promises and deals with them together. 

Below will not log until all promises have been resolved (e.g. 3000 ms).

```
const promise2 = new Promise ((resolve, reject)=> {
	setTimeout(resolve,100, "Hii")
})

const promise3 = new Promise ((resolve, reject)=> {
	setTimeout(resolve,1000, "Plopface")
})

const promise4 = new Promise ((resolve, reject)=> {
	setTimeout(resolve,3000, "u smell")
})


Promise.all([promise,promise2,promise3,promise4])
	.then(values=> {
		console.log(values);
	})
Promise {<pending>}
VM118:16 (4) ["Stuff worked", "Hii", "Plopface", "u smell"]

```

Another example: 

```
const urls = [

	'https://jsonplaceholder.typicode.com/users',
	'https://jsonplaceholder.typicode.com/posts',
	'https://jsonplaceholder.typicode.com/albums'
]

Promise.all(urls.map(url=> {
	return fetch(url).then(resp=>resp.json())

})).then(results=>{
	console.log(results[0])
	console.log(results[1])
	console.log(results[2])
}).catch(() => console.log('error'))

<
Promise {<pending>}__proto__: Promise[[PromiseStatus]]: "resolved"[[PromiseValue]]: undefined
VM215:12 (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
VM215:13 (100) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
VM215:14 (100) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]

```
This pulls the 3 pieces of JSON data from the websites. Note catch is added to end, to catch any errors.

Promise can only suceed or fail once. 
