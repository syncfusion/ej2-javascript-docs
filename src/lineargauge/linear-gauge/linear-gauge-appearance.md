---
title: " Appearance in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Appearance of Syncfusion EJ2 Linear Gauge component and more."
---

# Appearance in EJ2 Linear Gauge

## Customizing the Linear Gauge area

The following properties are available in the [`LinearGauge`](../api/linear-gauge/) to customize the Linear Gauge area.

* [`background`](../api/linear-gauge/#background) - Applies the background color for the Linear Gauge.
* [`border`](../api/linear-gauge/#border) - To customize the color and width of the border in Linear Gauge.
* [`margin`](../api/linear-gauge/#margin) - To customize the margins of the Linear Gauge.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5Background" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    background: 'skyblue',
    border: {
        color: "#FF0000",
        width: 2
    },
    margin: {
        left: 40,
        right: 40,
        top: 40,
        bottom: 40
    }
}, '#element');

```

{% endtab %}

## Setting up the Linear Gauge title

The title for the Linear Gauge can be set using [`title`](../api/linear-gauge/#title) property in Linear Gauge. Its appearance can be customized using the [`titleStyle`](../api/linear-gauge/#titlestyle) with the below properties.

* [`color`](../api/linear-gauge/fontModel/#color) - Specifies the text color of the title.
* [`fontFamily`](../api/linear-gauge/fontModel/#fontfamily) - Specifies the font family of the title.
* [`fontStyle`](../api/linear-gauge/fontModel/#fontstyle) - Specifies the font style of the title.
* [`fontWeight`](../api/linear-gauge/fontModel/#fontweight) - Specifies the font weight of the title.
* [`opacity`](../api/linear-gauge/fontModel/#opacity) - Specifies the opacity of the title.
* [`size`](../api/linear-gauge/fontModel/#size) - Specifies the font size of the title.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5TitleCustomization" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
        /Title for linear gauge
        title: 'linear gauge',
        titleStyle: {
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '23px'
        }
}, '#element');

```

{% endtab %}

## Customizing the Linear Gauge container

The area used to render the ranges and pointers at the center position of the gauge is called container. It is of three types namely

* Normal
* Rounded Rectangle
* Thermometer

The type of the container can be modified by using the [`type`](../api/linear-gauge/containerModel/#type) property in [`container`](../api/linear-gauge/#container). The container can be customized by using the following properties in [`container`](../api/linear-gauge/#container).

* [`offset`](../api/linear-gauge/containerModel/#offset) - To place the container with the specified distance from the axis of the Linear Gauge.
* [`width`](../api/linear-gauge/containerModel/#width) - To set the thickness of the container.
* [`height`](../api/linear-gauge/containerModel/#height) - To set the length of the container.
* [`backgroundColor`](../api/linear-gauge/containerModel/#backgroundcolor) - To set the background color of the container.
* [`border`](../api/linear-gauge/containerModel/#border) - To set the color and width for the border of the container.

### Normal

The "**Normal**" type will render the container as a rectangle and this is the default container type.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5NormalContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    container: {
        width: 30
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}

### Rounded Rectangle

The "**RoundedRectangle**" type will render the container as a rectangle with rounded corner radius. The rounded corner radius of the container can be customized using the [`roundedCornerRadius`](../api/linear-gauge/containerModel/#roundedcornerradius) property in [`container`](../api/linear-gauge/#container).

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5RoundedContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    container: {
        width: 30,
        type: 'RoundedRectangle'
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}

### Thermometer

The "**Thermometer**" type will render the container similar to the appearance of thermometer.

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5ThermometerContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    container: {
        width: 30,
        type: 'Thermometer'
    },
    axes: [{
        pointers: [{
            value:50,
            width:15,
            type:'Bar'
        }]
    }]
}, '#element');

```

{% endtab %}

## Fitting the Linear Gauge to the control

The Linear Gauge component is rendered with margin by default. To remove the margin around the Linear Gauge, the [`allowMargin`](../api/linear-gauge/#allowmargin) property in [`LinearGauge`](../api/linear-gauge/) is set as "**false**".

{% tab template= "linear-gauge/lineargauge-appearance", sourceFiles="index.ts,index.html", es5Template="es5ThermometerContainer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    allowMargin: false,
    background: "skyblue",
    border: {
        width: 3,
        color: "red"
    },
    margin: {
        left: 0,
        right: 0,
        top: 0,
        bottom: 0
    }
    axes: [{
    }]
}, '#element');

```

{% endtab %}

> Note: To use this feature, set the [`allowMargin`](../api/linear-gauge/#allowmargin) property to "**false**", the [`width`](../api/linear-gauge/#width) property to "**100%**" and the properties of [`margin`](../api/linear-gauge/#margin) to "**0**".