### Make stuff bounce off walls

```js
  //create
  const div  = {
			el: HTMLElement,
			dx: Math.random() * 3,
			dy: Math.random() * 3,
			speed: Math.random() + 0.75,
			moving: true,
			x: Math.random() * width - 50,
			y: Math.random() * height - 50,
			z: 1
		};

    //in animation loop
		divs.forEach(div => {
			const yBound = 100;
			const xBound = 100;

			if (div.moving) {
				if (div.y + div.dy > height - yBound || div.y + div.dy < 0) {
					div.dy = -div.dy;
				}

				if (div.x + div.dx > width - xBound || div.x + div.dx < 0) {
					div.dx = -div.dx;
				}

				div.x += div.dx;
				div.y += div.dy;

				div.el.style.transform = `
        translateX(${div.x}px)
        translateY(${div.y}px)
        translateZ(${div.z}px)`;
			} else {
				return null;
			}
```
