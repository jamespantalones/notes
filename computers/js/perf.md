## Performance stuff

### defer work
```js
export const deferWork = fn => {
	if (typeof requestIdleCallback !== 'undefined') {
		window.requestIdleCallback(fn, { timeout: 60 });
	} else if (typeof requestAnimationFrame !== 'undefined') {
		window.requestAnimationFrame(fn);
	} else {
		window.setTimeout(fn, 16.66);
	}

	return true;
};

```

and called like: `deferWork(() => window.localStorage.setItem('some_key', src))`


### check if item in viewport with Intersection Observer
```js
const PULLQUOTES = document.getElementsByClassName('pullquote');

function init() {
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.intersectionRatio > 0) {
        entry.target.classList.add('active');
        //remove from observation
        observer.unobserve(entry.target);
      }
    });
  });

  for (let i = 0; i < PULLQUOTES.length; i++) {
    observer.observe(PULLQUOTES[i]);
  }
}

export { init };
```
