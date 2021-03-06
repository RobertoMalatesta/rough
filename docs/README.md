# Rough.js

<b>Rough.js</b> is a light weight (~8k), [Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) based library that lets you draw in a _sketchy_, _hand-drawn-like_, style.
The library defines primitives to draw lines, curves, arcs, polygons, circles, and ellipses. It also supports drawing [SVG paths](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths).

![Rough.js sample](https://roughjs.com/images/cap_demo.png)

## Install

The latest Rough.js can be downloaded from the [dist folder](https://github.com/pshihn/rough/tree/master/dist).

or from npm:

```
npm install --save roughjs
```

## Usage

![Rough.js rectangle](https://roughjs.com/images/main/m1.png)

```js
const rc = rough.canvas(document.getElementById('canvas'));
rc.rectangle(10, 10, 200, 200); // x, y, width, height
```

### Lines and Ellipses

![Rough.js rectangle](https://roughjs.com/images/main/m2.png)

```js
rc.circle(80, 120, 50); // centerX, centerY, diameter
rc.ellipse(300, 100, 150, 80); // centerX, centerY, width, height
rc.line(80, 120, 300, 100); // x1, y1, x2, y2
```

### Filling

![Rough.js rectangle](https://roughjs.com/images/main/m3.png)

```js
rc.circle(50, 50, 80, { fill: 'red' }); // fill with red hachure
rc.rectangle(120, 15, 80, 80, { fill: 'red' });
rc.circle(50, 150, 80, {
  fill: "rgb(10,150,10)",
  fillWeight: 3 // thicker lines for hacure
});
rc.rectangle(220, 15, 80, 80, {
  fill: 'red',
  hachureAngle: 60, // angle of hachure,
  hachureGap: 8
});
rc.rectangle(120, 105, 80, 80, {
  fill: 'rgba(255,0,200,0.2)',
  fillStyle: 'solid' // solid fill
});
```

### Sketching style

![Rough.js rectangle](https://roughjs.com/images/main/m4.png)

```js
rc.rectangle(15, 15, 80, 80, { roughness: 0.5, fill: 'red' });
rc.rectangle(120, 15, 80, 80, { roughness: 2.8, fill: 'blue' });
rc.rectangle(220, 15, 80, 80, { bowing: 6, stroke: 'green', strokeWidth: 3 });
```

### SVG Paths

![Rough.js rectangle](https://roughjs.com/images/main/m5.png)

```js
rc.path('M80 80 A 45 45, 0, 0, 0, 125 125 L 125 80 Z', { fill: 'green' });
rc.path('M230 80 A 45 45, 0, 1, 0, 275 125 L 275 80 Z', { fill: 'purple' });
rc.path('M80 230 A 45 45, 0, 0, 1, 125 275 L 125 230 Z', { fill: 'red' });
rc.path('M230 230 A 45 45, 0, 1, 1, 275 275 L 275 230 Z', { fill: 'blue' });
```

SVG Path with simplification:

![Rough.js rectangle](https://roughjs.com/images/main/m9.png) ![Rough.js rectangle](https://roughjs.com/images/main/m10.png)

## Using web workers

If you have [Workly](https://github.com/pshihn/workly) imported on your web page (~1k only), RoughJS will automatically offload all processing to a web worker - freeing up your main UI thread. This is great when creating complex drawings using RoughJs like maps. Read more about it [here](https://github.com/pshihn/rough/wiki/RoughJS-in-a-web-worker).

```html
<script src="https://cdn.jsdelivr.net/gh/pshihn/workly/dist/workly.min.js"></script>
<script src="../../dist/rough.min.js"></script>
```

![Rough.js map](https://roughjs.com/images/main/m6.png)

(source code for this map in examples)

## Examples

[View examples here](https://github.com/pshihn/rough/wiki/Examples)

## API & Documentation

[Full Rough.js API](https://github.com/pshihn/rough/wiki)

## Credits

Some of the core algorithms were adapted from [handy](https://www.gicentre.net/software/#/handy/) processing lib.

## License
[MIT License](https://github.com/pshihn/rough/blob/master/LICENSE) (c) [Preet Shihn](https://twitter.com/preetster)
