## Full bleed video

```js
  resize: function(){
    let width = window.innerWidth;
    let height = window.innerHeight;

    let pWidth = window.innerWidth;
    let pHeight = pWidth / ( 16 / 9 );

    let ratio = 16 / 9;


    //gap underneath
    if (width / ratio < height){
      pWidth = Math.ceil(height * ratio);

      player.style.position = 'fixed';
      player.style.width = pWidth + 'px';
      player.style.height = height + 'px';
      player.style.top = 0;
      player.style.left = (width - pWidth) / 2 + 'px';
      player.style.zIndex = 0;

    }

    //gap on side
    else{
      pHeight = Math.ceil(width / ratio);

      player.style.position = 'fixed';
      player.style.width = width + 'px';
      player.style.height = pHeight + 'px';
      player.style.left = 0;
      player.style.top = (height - pHeight) / 2 + 'px';
      player.style.zIndex = 0;

    }
  }
```
