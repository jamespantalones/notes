## Performance stuff

### defer work
```js
function deferWork() {
  if ((typeof requestIdleCallback as any) !== 'undefined') {
    requestIdleCallback(fn, { timeout: 60 });
  } else if (typeof requestAnimationFrame !== 'undefined') {
    requestAnimationFrame(fn);
  } else {
    setTimeout(fn, 16.66);
  }
}
```
