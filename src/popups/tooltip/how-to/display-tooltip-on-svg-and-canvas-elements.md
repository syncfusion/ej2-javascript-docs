# Display tooltip on SVG and canvas elements

Tooltip can be displayed on both SVG and Canvas elements. You can directly attach the `<svg>` or `<canvas>` elements to show tooltips on data visualization elements.

## SVG

Create the SVG square element and refer to the following code snippet to render the tooltip on SVG square.

```typescript
let square: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'SVG Square',
    target: '#square
});
square.appendTo('#box');
```

## Canvas

Create the canvas circle element and refer to the following code snippet to render the tooltip on Canvas circle.

```typescript
let circle: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'Canvas Circle',
    target: '#circle'
});
circle.appendTo('#box');
```

{% tab template="tooltip/svg-canvas", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="svg-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';

//Render tooltip component
let square: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'SVG Square',
    target: '#square'
});
square.appendTo('#box');

let ellipse: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'SVG Ellipse',
    target: '#ellipse'
});
ellipse.appendTo('#box');

let polyline: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'SVG Polyline',
    target: '#polyline'
});
polyline.appendTo('#box');

let circle: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'Canvas Circle',
    target: '#circle'
});
circle.appendTo('#box');

let triangle: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'Canvas Triangle',
    target: '#triangle'
});

triangle.appendTo('#box');
let canvas: HTMLCanvasElement = document.getElementById('triangle') as HTMLCanvasElement;
let context;
if (canvas.getContext) {
    context = canvas.getContext('2d');
    context.beginPath();
    context.moveTo(0, 50);
    context.lineTo(100, 50);
    context.lineTo(50, 0);
    context.fillStyle = "#FDA600";
    context.fill();
}
canvas = document.getElementById('circle') as HTMLCanvasElement;
context = canvas.getContext('2d');
let centerX: number = canvas.width / 2;
let centerY: number = canvas.height / 2;
let radius: number = 30;
context.beginPath();
context.arc(centerX, centerY, radius, 0, 2 * Math.PI, false);
context.fillStyle = '#0450C2';
context.fill();

```

{% endtab %}