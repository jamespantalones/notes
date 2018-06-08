### normalize mouse coords

```glsl
vec2 mouse_norm = vec2( m.x/screen.width, 1.0 - m.y/screen.height )
```


### vanilla webgl with uniform update
#### (ripped from a typescript project of mine, and this file has VERY lazy typescript)

```js
//----------------------------------
//
// Shader BG
//
//----------------------------------

import createVertextShader from './vertex';
import createFragmentShader from './fragment';

export default class SceneInstance {
  public el: HTMLDivElement;
  public canvas: HTMLCanvasElement;
  public gl: any;
  public program: any;

  public delta = 1.0;

  constructor(el: HTMLDivElement) {
    this.el = el;
    this.render = this.render.bind(this);
    this.init();
  }

  public init() {
    this.canvas = document.createElement('canvas');
    this.canvas.width = window.innerWidth;
    this.canvas.height = window.innerHeight;
    this.el.appendChild(this.canvas);

    this.createContext();
  }

  public createContext() {
    this.gl =
      this.canvas.getContext('webgl') || this.canvas.getContext('experimental-webgl');

    // black clear color
    this.gl.clearColor(0.0, 0.0, 0.0, 1.0);
    this.gl.enable(this.gl.DEPTH_TEST);
    this.gl.depthFunc(this.gl.LEQUAL);
    this.gl.clear(this.gl.COLOR_BUFFER_BIT);
    this.program = this.gl.createProgram();

    this.addShader(
      this.gl,
      this.program,
      this.gl.createShader(this.gl.VERTEX_SHADER),
      createVertextShader,
    );

    this.addShader(
      this.gl,
      this.program,
      this.gl.createShader(this.gl.FRAGMENT_SHADER),
      createFragmentShader,
    );

    this.gl.linkProgram(this.program);

    if (!this.gl.getProgramParameter(this.program, this.gl.LINK_STATUS)) {
      console.error(
        `Unable to init the shader program: ${this.gl.getProgramInfoLog(this.program)}`,
      );
    }

    this.gl.useProgram(this.program);

    this.render();
  }

  public render() {
    this.delta += 0.1;
    const uTime = this.gl.getUniformLocation(this.program, 'u_time');
    this.gl.uniform1f(uTime, this.delta);

    // set billboard geometry
    this.attributeSetFloats(this.gl, this.program, 'vertexPosition', 3, [
      1.0,
      1.0,
      0.0,
      -1.0,
      1.0,
      0.0,
      1.0,
      -1.0,
      0.0,
      -1.0,
      -1.0,
      0.0,
    ]);

    this.attributeSetFloats(this.gl, this.program, 'vertexColor', 4, [
      1.0,
      1.0,
      1.0,
      1.0,
      1.0,
      0.0,
      0.0,
      1.0,
      0.0,
      1.0,
      0.0,
      1.0,
      0.0,
      0.0,
      1.0,
      1.0,
    ]);

    this.gl.drawArrays(this.gl.TRIANGLE_STRIP, 0, 4);

    requestAnimationFrame(this.render);
  }

  public addShader(gl: any, program: any, shader: any, source: string) {
    gl.shaderSource(shader, source);
    gl.compileShader(shader);
    if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
      console.error(gl.getShaderInfoLog(shader));
    }

    gl.attachShader(program, shader);
  }

  public attributeSetFloats(
    gl: any,
    program: any,
    attributeName: any,
    itemSize: any,
    items: any,
  ) {
    gl.bindBuffer(gl.ARRAY_BUFFER, gl.createBuffer());
    gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(items), gl.STATIC_DRAW);

    const attributeLocation = gl.getAttribLocation(program, attributeName);
    gl.enableVertexAttribArray(attributeLocation);
    gl.vertexAttribPointer(attributeLocation, itemSize, gl.FLOAT, false, 0, 0);
  }
}

```
