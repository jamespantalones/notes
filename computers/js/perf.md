## Performance stuff

### defer work
```js
function deferWork(fn) {
  if ((typeof requestIdleCallback as any) !== 'undefined') {
    requestIdleCallback(fn, { timeout: 60 });
  } else if (typeof requestAnimationFrame !== 'undefined') {
    requestAnimationFrame(fn);
  } else {
    setTimeout(fn, 16.66);
  }
}
```

and called like: `deferWork(() => window.localStorage.setItem('some_key', src))`
