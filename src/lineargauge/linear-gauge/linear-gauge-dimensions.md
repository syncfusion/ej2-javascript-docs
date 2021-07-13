---
title: "Dimensions in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Dimensions of Syncfusion EJ2 Linear Gauge component and more."
---

# Dimensions in EJ2 Linear Gauge

## Size for Linear Gauge

The height and width of the Linear Gauge can be set using the [`width`](../api/linear-gauge/#width) and [`height`](../api/linear-gauge/#height) properties in Linear Gauge.

### In Pixel

The size of the Linear Gauge can be set in pixel as demonstrated below.

{% tab template= "linear-gauge/lineargauge-dimensions", sourceFiles="index.ts,index.html", es5Template="es5SizeInPixel" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    width: '650px',
    height: '350px'
}, '#element');

```

{% endtab %}

### In Percentage

By setting value in percentage, Linear Gauge receives its dimension matching to its parent. For example, when the height is set as "**50%**", Linear Gauge renders to half of the parent height. The Linear Gauge will be responsive when the width is set as "**100%**".

```html
    <div id='container'>
        <div id='element' style="width:1000px; height:600px;"></div>
    </div>
```

{% tab template= "linear-gauge/lineargauge-dimensions", sourceFiles="index.ts,index.html", es5Template="es5SizeInPercentage" %}

```typescript

import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    width: '100%',
    height: '50%'
}, '#element');

```

{% endtab %}

>Note: When the component's size is not specified, the height will be "**450px**" and the width will be the same as the parent element's width.