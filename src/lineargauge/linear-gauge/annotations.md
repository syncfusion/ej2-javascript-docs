---
title: " Annotations in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about Annotations feature of Syncfusion EJ2 Linear Gauge component and more."
---

# Annotations in EJ2 Linear Gauge

<!-- markdownlint-disable MD013 -->

Annotations are used to mark the specific area of interest in the Linear Gauge with text, HTML elements, or images. Any number of annotations can be added to the Linear Gauge component.

## Adding annotation

To render the custom HTML elements in the Linear Gauge component, use the [`content`](../api/linear-gauge/annotation/#content) property in the [`annotations`](../api/linear-gauge/annotation). The annotation can be rendered either by specifying the id of the element or specifying the code to create a new element that needs to be displayed in the gauge area.

<!-- markdownlint-disable MD036 -->

 ```html
<script id='fruits' type="text/x-template">
    <div id='apple'>
        <img src='src/lineargauge/images/apple.png'>
    </div>
</script>

```

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
        content: '#fruits',
        x: 100,
        y: 100
    }]
}, '#element');

```

## Customization

The following properties are used to customize the annotation.

* [`zIndex`](../api/linear-gauge/annotation/#zindex) - This property is used to bring the annotation to the front or back, when annotation overlaps with another element.
* [`axisValue`](../api/linear-gauge/annotation/#axisvalue) - This property is used to place the annotation in the specified axis value with respect to the provided axis index.
* [`axisIndex`](api/linear-gauge/annotation/#axisindex) - This property is used to place the annotation in the specified axis with respect to the provided axis value.
* [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment) - This property is used to place the annotation horizontally.
* [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment) - This property is used to place the annotation vertically.
* [`x`](../api/linear-gauge/annotation/#x), [`y`](../api/linear-gauge/annotation/#y) - This property is used to place the annotation in the specified location.

### Changing the z-index

To change the stack order of an annotation element, the [`zIndex`](../api/linear-gauge/annotation/#zindex) property of the [`annotations`](../api/linear-gauge/annotation) can be used.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Annotation" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
     annotations: [{
       content: '<div id="first"><h1>Gauge</h1></div>',
       verticalAlignment: 'Center',
       horizontalAlignment: 'Center',
       zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

### Positioning an annotation

The annotation can be placed anywhere in the Linear Gauge by setting the pixel value to the [`x`](../api/linear-gauge/annotation/#x) and [`y`](../api/linear-gauge/annotation/#y) properties in the [`annotations`](../api/linear-gauge/annotation).

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Position" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
        content: '<div id="first"><h1>Gauge</h1></div>',
        x: 100,
        y: 100,
        zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

### Alignment of annotation

The annotation can be aligned horizontally and vertically by using [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment) and [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment) properties respectively. The possible values can be "**Center**", "**Far**", "**Near**", and "**None**". The [`horizontalAlignment`](../api/linear-gauge/annotation#horizontalalignment) and [`verticalAlignment`](../api/linear-gauge/annotation#verticalalignment) properties are not applicable when the [`x`](../api/linear-gauge/annotation/#x) and [`y`](../api/linear-gauge/annotation/#y) properties are set in the [`annotations`](../api/linear-gauge/annotation).

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5Alignment" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
       content: '<div id="first"><h1>Gauge</h1></div>',
       verticalAlignment: 'Center',
       horizontalAlignment: 'Center',
       zIndex: '1'
    }]
}, '#element');

```

{% endtab %}

## Multiple annotations

Multiple annotations can be added to the Linear Gauge component by adding the multiple [`annotation`](../api/linear-gauge/annotation) objects in the [`annotations`](../api/linear-gauge/#annotations) and customization for the annotation can be done with the [`annotation`](../api/linear-gauge/annotation) object.

{% tab template= "linear-gauge/annotations", sourceFiles="index.ts,index.html", es5Template="es5MultipleAnnotation" %}

```typescript

import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
      annotations: [
            {
                content: '<div><h1 style="color:red;">Speed</h1></div>',
                verticalAlignment: 'Near',
                horizontalAlignment: 'Center',
                x: 100,
                y: 150,
                zIndex: '1'
            },
            {
                content: '<div><h1 style="color:blue;">Meter</h1></div>',
                verticalAlignment: 'Center',
                horizontalAlignment: 'Center',
                x: -100,
                y: -100,
                zIndex: '1'
            }]
}, '#element');

```

{% endtab %}