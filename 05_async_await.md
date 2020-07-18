Async await is part of ES8 and is built on top of promises.

Async code example:
```
movePlayer(100,'Left')
  .then(() => movePlayer(400, 'Left'))
   .then(() => movePlayer(10, 'Right'))
     .then(() => movePlayer(330, 'Left'))
```
Async await would look like this:
```
async function playerStart () {
  const first = movePlayer(100,'Left')
  const second = await movePlayer(400, 'Left'))
  await movePlayer(10, 'Right'))
  await movePlayer(330, 'Left'))
}
```
Syntatic sugar- does same thing as Promises just make it look prettier.

```
>fetch ('https://jsonplaceholder.typicode.com/users')
  .then(resp => resp.json())
  .then(console.log)
<Promise {<pending>}
(10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
```
Do this async await:
```
async function fetchUsers () {
  const response = await fetch ('https://jsonplaceholder.typicode.com/users')
  const data = await response.json();
  console.log(data);
}

>fetchUsers()
<Promise {<pending>}
VM110:4 (10) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]

```
Another example with try catch error method & Uses destructuring on const (ES6?).:
```
const urls = [
  'https://jsonplaceholder.typicode.com/users',
  'https://jsonplaceholder.typicode.com/posts',
  'https://jsonplaceholder.typicode.com/albums'
]

const getData = async function () {
  try{
    const [users, posts, albums] = await Promise.all(urls.map(url=> {
    return fetch(url).then(resp=>resp.json())
  }))
  console.log('users',users)
  console.log('posts',posts)
  console.log('albums',albums)
  } catch(err) {
    console.log('error', err)
  }
}

>getData()
<Promise {<pending>}
VM111:10 GET https://jsonplaceholde.typicode.com/users net::ERR_NAME_NOT_RESOLVED
(anonymous) @ VM111:10
getData @ VM111:9
(anonymous) @ VM115:1
VM111:16 error TypeError: Failed to fetch
```
