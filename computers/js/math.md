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

```js
function lerp (start, end, amt){
  return (1-amt)*start+amt*end
}
```

### generate an ID
```js
export const generateId = () => {
  let S4 = function() {
    return (((1 + Math.random()) * 0x10000) | 0).toString(16).substring(1);
  };

  return S4() + S4();
};
```
