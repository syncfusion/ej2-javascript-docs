# Legend

Legend provides valuable information for interpreting what the circular gauge axis range displays, and they can be represented in various colors, shapes, and other identifiers based on the data. It gives a breakdown of what each symbol represents in the axis range of circular gauge.

You can add the legend for circular gauge ranges by setting the visible property of `legendSettings` to true.

## Legend customization

Customization option is also provided for the legend shape, alignment, and position.

### Position and alignment

The position of the legend is used to place legend in various positions. You can use the `position` property in `legendSettings`. Based on the position, the legend item will be aligned. The following options are available to customize the legend position:

* Top

* Bottom

* Left

* Right

* Custom

* Auto

The legend alignment is used to align the legend items in specific location. You can use the alignment property in [`legendSettings`](../api/circular-gauge/legendSettings) to align the legend items. The following options are available to customize the legend alignment:

* Near

* Center

* Far

The legends can also be positioned to absolute position using the `location.x` and `location.y` properties available in `legendSettings`.

### Legend size

The legend size can be modified using the `height` and `width` properties in `legendSettings`.

### Legend opacity

To specify the transparency for legend shape, set the `opacity` property in `legendSettings`.

### Legend shape

To change the legend item shape, specify the desired shape in the `shape` property of the legend. By default, the shape of the legend is `circle`.

It also supports the following shapes:

* Circle

* Rectangle

* Diamond

* Triangle

* InvertedTriangle

* Image

You can customize a shape using the `shapeWidth` and `shapeHeight` properties.

### Legend padding

You can control the spacing between the legend items using the `padding` option of the legend. The default value of padding is 5.

### Legend border

You can customize the legend border using the border option in the legend. The legend border can be customized using the border `color` and `width` properties.

<!-- markdownlint-disable MD009 -->

### Font of the legend text

The font of the legend item text can be customized using the following properties:

* fontFamily

* fontStyle

* fontWeight 

* opacity

* color 

* size

The following code example shows how to add legend in the gauge.

{% tab template= "circular-gauge/gauge-legend", sourceFiles="index.ts,index.html", es5Template="es5Legend" %}

```typescript

import { CircularGauge, Legend } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Legend);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        majorTicks: {
            useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
            useRangeColor: true
        },

        ranges: [{
            start: 0,
            end: 25,
            radius: '108%'
        },{
            start: 25,
            end: 50,
            radius: '108%'
        },{
            start: 50,
            end: 75,
            radius: '108%'
        },{
            start: 75,
            end: 100,
            radius: '108%'
        }]
    }],
     legendSettings : {
        visible: true,
        shapeWidth:30,
        shapeHeight:30,
        padding:15,
        border: {
            color:'green',
            width:3
        }
    }
});
gauge.appendTo('#element');

```

{% endtab %}

## Toggle option in legend

The toggle option has been provided for legend. So, if you toggle the legend, the given color will be changed to the corresponding circular gauge range. You can enable the toggle option using [`toggleVisibility`]((../api/circular-gauge/legendSettings-toggleVisibility-boolean)) in the `legendSettings` property.

{% tab template= "circular-gauge/gauge-legend", sourceFiles="index.ts,index.html", es5Template="es5ToggleLegend" %}

```typescript

import { CircularGauge, Legend } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Legend);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        majorTicks: {
            useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
            useRangeColor: true
        },
        ranges: [{
            start: 0,
            end: 25,
            radius: '108%'
        },{
            start: 25,
            end: 50,
            radius: '108%'
        },{
            start: 50,
            end: 75,
            radius: '108%'
        },{
            start: 75,
            end: 100,
            radius: '108%'
        }]
    }],
    legendSettings : {
        visible: true,
        toggleVisibility: true
    }
});
gauge.appendTo('#element');

```

{% endtab %}

## Paging support in legend

By default, paging will be enabled if the legend items exceed the legend bounds. You can view each legend item by navigating between the pages using navigation buttons.

{% tab template= "circular-gauge/gauge-legend", sourceFiles="index.ts,index.html", es5Template="es5LegendPaging" %}

```typescript

import { CircularGauge, Legend } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Legend);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        majorTicks: {
            useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
        useRangeColor: true
        },
        ranges: [{
            start: 0,
            end: 25,
            radius: '108%'
        },{
            start: 25,
            end: 50,
            radius: '108%'
        },{
            start: 50,
            end: 75,
            radius: '108%'
        },{
            start: 75,
            end: 100,
          radius: '108%'
        }]
    }],
    legendSettings : {
        visible: true,
        height: '50'
    }
});
gauge.appendTo('#element');

```

{% endtab %}

## Legend text customization

You can customize the legend text using [`legendText`](../api/circular-gauge/range/#legendtext) property in `ranges`.

{% tab template= "circular-gauge/gauge-legend", sourceFiles="index.ts,index.html", es5Template="es5LegendText" %}

```typescript

import { CircularGauge, Legend, ILegendRenderEventArgs } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Legend);
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        majorTicks: {
            useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
            useRangeColor: true
        },
        ranges: [{
            start: 0,
            end: 25,
            radius: '108%',
            legendText: 'light air'
        },{
            start: 25,
            end: 50,
            radius: '108%',
            legendText: 'light air'
        },{
            start: 50,
            end: 75,
            radius: '108%',
            legendText: 'light breeze'

        },{
            start: 75,
            end: 100,
            radius: '108%',
            legendText: 'Gentle breeze'
        }]
    }],
    legendSettings : {
        visible: true
    },
    legendRender: (args: ILegendRenderEventArgs) => {
        args.text = "Legend Modified Text Value";
    }
});
gauge.appendTo('#element');

```

{% endtab %}

`legendRendering` event will be triggered before rendering each legend item, using this event you can customize needed legend items using following arguments.

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|   fill               |   Specifies the legend shape color  |
|   text               |   Specifies the current legend text   |
|   shape            | Customize the shape of the legends  |
| name | Specifies the name of the event  |
|cancel |  Set to true, to cancel the event status