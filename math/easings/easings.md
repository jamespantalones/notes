### Linear

```js
Math.linearTween = function(t, b, c, d) {
  return c * t / d + b;
};
```

### Quad In

```js
Math.easeInQuad = function(t, b, c, d) {
  t /= d;
  return c * t * t + b;
};
```

### Quad Out

```js
Math.easeOutQuad = function(t, b, c, d) {
  t /= d;
  return -c * t * (t - 2) + b;
};
```

### Quad In/Out

```js
Math.easeInOutQuad = function(t, b, c, d) {
  t /= d / 2;
  if (t < 1) return c / 2 * t * t + b;
  t--;
  return -c / 2 * (t * (t - 2) - 1) + b;
};
```

### Cubic In

```js
Math.easeInCubic = function(t, b, c, d) {
  t /= d;
  return c * t * t * t + b;
};
```

### Cubic Out

```js
Math.easeOutCubic = function(t, b, c, d) {
  t /= d;
  t--;
  return c * (t * t * t + 1) + b;
};
```

### Cubic In/Out

```js
Math.easeInOutCubic = function(t, b, c, d) {
  t /= d / 2;
  if (t < 1) return c / 2 * t * t * t + b;
  t -= 2;
  return c / 2 * (t * t * t + 2) + b;
};
```

### Quartic In

```js
Math.easeInQuart = function(t, b, c, d) {
  t /= d;
  return c * t * t * t * t + b;
};
```

### Quartic Out

```js
Math.easeOutQuart = function(t, b, c, d) {
  t /= d;
  t--;
  return -c * (t * t * t * t - 1) + b;
};
```

### Quartic In/Out

```js
Math.easeInOutQuart = function(t, b, c, d) {
  t /= d / 2;
  if (t < 1) return c / 2 * t * t * t * t + b;
  t -= 2;
  return -c / 2 * (t * t * t * t - 2) + b;
};
```

### Sine In

```js
Math.easeInSine = function(t, b, c, d) {
  return -c * Math.cos(t / d * (Math.PI / 2)) + c + b;
};
```

### Sine Out

```js
Math.easeOutSine = function(t, b, c, d) {
  return c * Math.sin(t / d * (Math.PI / 2)) + b;
};
```

### Sine In/Out

```js
Math.easeInOutSine = function(t, b, c, d) {
  return -c / 2 * (Math.cos(Math.PI * t / d) - 1) + b;
};
```

### Expo In

```js
Math.easeInExpo = function(t, b, c, d) {
  return c * Math.pow(2, 10 * (t / d - 1)) + b;
};
```

### Expo Out

```js
Math.easeOutExpo = function(t, b, c, d) {
  return c * (-Math.pow(2, -10 * t / d) + 1) + b;
};
```

### Expo In/Out

```js
Math.easeInOutExpo = function(t, b, c, d) {
  t /= d / 2;
  if (t < 1) return c / 2 * Math.pow(2, 10 * (t - 1)) + b;
  t--;
  return c / 2 * (-Math.pow(2, -10 * t) + 2) + b;
};
```

### Circular In

```js
Math.easeInCirc = function(t, b, c, d) {
  t /= d;
  return -c * (Math.sqrt(1 - t * t) - 1) + b;
};
```

### Circular Out

```js
Math.easeOutCirc = function(t, b, c, d) {
  t /= d;
  t--;
  return c * Math.sqrt(1 - t * t) + b;
};
```

### Circular In/Out

```js
Math.easeInOutCirc = function(t, b, c, d) {
  t /= d / 2;
  if (t < 1) return -c / 2 * (Math.sqrt(1 - t * t) - 1) + b;
  t -= 2;
  return c / 2 * (Math.sqrt(1 - t * t) + 1) + b;
};
```
