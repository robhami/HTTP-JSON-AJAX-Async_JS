// Solve the questions below:

// #1) Create a promise that resolves in 4 seconds and returns "success" string
```
const promise = new Promise ((resolve, reject)=> {

	setTimeout (() => {
		resolve("success");
	}, 4000)
});
promise.then(result => console.log(result));
```

// #2) Run the above promise and make it console.log "success"
promise.then(result => console.log(result));

// #3) Read about Promise.resolve() and Promise.reject(). How can you make
// the above promise shorter with Promise.resolve() and console loggin "success"
```
const promise = Promise.resolve(
	setTimeout (() => {
		console.log("success");
	}, 4000)
);
```

// #4) Catch this error and console log 'Ooops something went wrong'
```
Promise.reject('failed')
.then(result=>result)
.catch(() => console.log("error!"))
```
// #5) Use Promise.all to fetch all of these people from Star Wars (SWAPI) at the same time.
// Console.log the output and make sure it has a catch block as well.
```
const urls = [
  'https://swapi.dev/api/people/1/',
  'https://swapi.dev/api/people/2/',
  'https://swapi.dev/api/people/3/',
  'https://swapi.dev/api/people/4/'
]

Promise.all(urls.map(url=> {
	return fetch(url)
	.then(response=>response.json())
})).then(results=>{
	console.log(results[0])
	console.log(results[1])
	console.log(results[2])
}).catch(() => console.log('error'))
```
// #6) Change one of your urls above to make it incorrect and fail the promise
// does your catch block handle it?
```
const urls = [
  'https://swapi.dev/api/peopl/1/',
  'https://swapi.dev/api/people/2/',
  'https://swapi.dev/api/people/3/',
  'https://swapi.dev/api/people/4/'
]

Promise.all(urls.map(url=> {
	return fetch(url)
	.then(response=>response.json())
})).then(results=>{
	console.log(results[0])
	console.log(results[1])
	console.log(results[2])
}).catch(() => console.log('error'))
Promise {<pending>}
VM100:9 GET https://swapi.dev/api/peopl/1/ 404
(anonymous) @ VM100:9
(anonymous) @ VM100:8
VM100:15 error
```
