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
Then run the promise and make it true?how?:

```
promise.then(result => console.log(result));
```
