## Some generic math stuff


### get random float between range
```js
export const randomFloat = (min, max) => {
  return Math.random() * (max - min) + min
}
```


### get random int between range
```js
export const randomInt = (min, max) => {
  return Math.floor(Math.random() * (max - min) + min)
}
```
