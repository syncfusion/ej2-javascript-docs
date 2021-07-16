---
title: " Events in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about Events of Syncfusion EJ2 Linear Gauge component and more."
---

# Events in EJ2 Linear Gauge

This section describes the Linear Gauge component's event that gets triggered when corresponding operations are performed.

## animationComplete

When the pointer animation is completed, the [`animationComplete`](../api/linear-gauge#animationcomplete) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAnimationCompleteEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5animationComplete" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
  animationComplete: function() {

  },
  axes:[{
        pointers:[{
            value: 10
        }]
    }]
}, '#element');
```

{% endtab %}

## annotationRender

Before the annotation is rendered in the Linear Gauge, the [`annotationRender`](../api/linear-gauge#annotationrender) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAnnotationRenderEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5AnnotationRender" %}

```typescript
import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
  annotationRender: function() {

  },
  annotations: [{
       content: '<div id="first"><h1>Gauge</h1></div>',
       verticalAlignment: 'Center',
       horizontalAlignment: 'Center',
       zIndex: '1'
  }]
}, '#element');
```

{% endtab %}

## axisLabelRender

Before each axis label is rendered in the Linear Gauge, the [`axisLabelRender`](../api/linear-gauge#axislabelrender) event is fired. To know more about the arguments of this event, refer [here](../api/linear-gauge/iAxisLabelRenderEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5AxisLabelRender" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
  axisLabelRender: function() {

  }
}, '#element');
```

{% endtab %}

## beforePrint

The [`beforePrint`](../api/linear-gauge/#beforeprint) event is fired before the print begins. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPrintEventArgs/).

{% tab template= "linear-gauge/lineargauge-print", sourceFiles="index.ts,index.html", es5Template="es5PrintEvent" %}

```typescript
import { LinearGauge, Print } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Print);

let gauge: LinearGauge = new LinearGauge({
  allowPrint: true,
  beforePrint: function() {
  }
}, '#element');

document.getElementById('print').onclick = () => {
    gauge.print();
};
```

{% endtab %}

## dragEnd

The [`dragEnd`](../api/linear-gauge#dragend) event will be fired before the pointer drag is completed. To know more about the argument of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5DragEnd" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 dragEnd: function() {
 },
 axes : [{
   pointers: [{
     enableDrag: true
   }]
 }]
}, '#element');
```

{% endtab %}

## dragMove

The [`dragMove`](../api/linear-gauge#dragmove) event will be fired when the pointer is dragged. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5DragMove" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 dragMove: function() {
 },
 axes : [{
   pointers: [{
     enableDrag: true
   }]
 }]
}, '#element');
```

{% endtab %}

## dragStart

When the pointer drag begins, the [`dragStart`](../api/linear-gauge#dragstart) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iPointerDragEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5DragStart" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 dragStart: function() {
 },
 axes : [{
   pointers: [{
     enableDrag: true
   }]
 }]
}, '#element');
```

{% endtab %}

## gaugeMouseDown

When mouse is pressed down on the gauge, the [`gaugeMouseDown`](../api/linear-gauge#gaugemousedown) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5GaugeMouseDown" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 gaugeMouseDown: function() {
 }
}, '#element');
```

{% endtab %}

## gaugeMouseLeave

When mouse pointer moves over the gauge, the [`gaugemouseleave`](../api/linear-gauge#gaugemouseleave) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5GaugeMouseLeave" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 gaugeMouseLeave: function() {
 }
}, '#element');
```

{% endtab %}

## gaugeMouseMove

When mouse pointer leaves the gauge, the [`gaugeMouseMove`](../api/linear-gauge#gaugemousemove) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5GaugeMouseMove" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 gaugeMouseMove: function() {
 }
}, '#element');
```

{% endtab %}

## gaugeMouseUp

When the mouse pointer is released over the Linear Gauge, the [`gaugeMouseUp`](../api/linear-gauge#gaugemouseup) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iMouseEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5GaugeMouseUp" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 gaugeMouseUp: function() {
 }
}, '#element');
```

{% endtab %}

## load

Before the Linear Gauge is loaded, the [`load`](../api/linear-gauge#load) event is fired. To know more about the arguments of this event, refer [here](../api/linear-gauge/iLoadEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5Load" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 load: function() {
 }
}, '#element');
```

{% endtab %}

## loaded

After the Linear Gauge has been loaded, the [`loaded`](../api/linear-gauge#loaded) event will be triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iLoadedEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5Loaded" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 loaded: function() {
 }
}, '#element');
```

{% endtab %}

## resized

After the window resizing, the [`resized`](../api/linear-gauge#resized) event is triggered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iResizeEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5Resized" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 resized: function() {
 }
}, '#element');
```

{% endtab %}

## tooltipRender

The [`tooltipRender`](../api/linear-gauge#tooltiprender) event is fired before the tooltip is rendered. To know more about the arguments of this event, refer [here](../api/linear-gauge/iTooltipRenderEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5TooltipChange" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
 tooltipRender: function() {
 },
 tooltip: {
   enable: true
 },
 axes: [{
   pointers: [{
     value: 40
   }]
 }]
}, '#element');
```

{% endtab %}

## valueChange

The [`valueChange`](../api/linear-gauge#valuechange) event is triggered when the pointer is dragged from one value to another. To know more about the arguments of this event, refer [here](../api/linear-gauge/iValueChangeEventArgs/).

{% tab template= "linear-gauge/events", sourceFiles="index.ts,index.html", es5Template="es5ValueChange" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
 valueChange: function() {
 },
 axes: [{
   pointers: [{
     enableDrag: true,
     value: 40
   }]
 }]
}, '#element');
```

{% endtab %}
