---
title: "Pyramid | TypeScript "

component: "Accumulation Chart"

description: "The pyramid chart displays series value as progressively decreasing amount to hundred percent in total"
---

# Pyramid Chart

To render a pyramid series, use the series [`type`](../api/accumulation-chart/accumulationSeriesModel/) as `Pyramid` and
inject `PyramidSeries` module using the `AccumulationChart.Inject(PyramidSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5AccPyramid" %}

```typescript

import { AccumulationChart, PyramidSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(PyramidSeries);

let chart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: [{ x: 'Australia', y: 20, text: 'Australia 20%' },
            { x: 'France', y: 22, text: 'France 22%' },
            { x: 'China', y: 23, text: 'China 23%' },
            { x: 'India', y: 24, text: 'India 24%' },
            { x: 'Japan', y: 25, text: 'Japan 25%' },
            { x: 'Germany', y: 27, text: 'Germany 27%' }],
        xName: 'x', yName: 'y',
        }],
}, '#element');

```

{% endtab %}

## Mode

The Pyramid chart supports linear and surface modes of rendering. The default type of the
`pyramidMode` is `linear`.

{% tab template= "chart/chart-types", es5Template="es5AccPyramidMode" %}

```typescript

import { AccumulationChart, PyramidSeries} from '@syncfusion/ej2-charts';
import { pyramidData } from './datasource.ts';
AccumulationChart.Inject(PyramidSeries);

let pyramidchart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: pyramidData,
        xName: 'x', yName: 'y',
        pyramidMode: 'Surface',
        }],
}, '#element');

```

{% endtab %}

## Size

The size of the pyramid chart can be customized by using the  `width` and `height` properties.

{% tab template= "chart/chart-types", es5Template="es5AccCust" %}

```typescript

import { AccumulationChart, PyramidSeries} from '@syncfusion/ej2-charts';
import { pyramidData } from './datasource.ts';
AccumulationChart.Inject(PyramidSeries);

let chart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: pyramidData,
        xName: 'x', yName: 'y',

        //Width of the pyramid will be 100% of the chart area
        width: '60%',

        //Height of the pyramid will be 100% of the chart area
        height: '80%',
        }],
}, '#element');

```

{% endtab %}

## Gap Between the Segments

Pyramid chart provides options to customize the space between the segments by using the `gapRatio` property of the
series. It ranges from 0 to 1.

{% tab template= "chart/chart-types", es5Template="es5AccGap" %}

```typescript

import { AccumulationChart, PyramidSeries} from '@syncfusion/ej2-charts';
import { pyramidData } from './datasource.ts';
AccumulationChart.Inject(PyramidSeries);

let pyramidchart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: pyramidData,
        xName: 'x', yName: 'y',
        // Defines the gap to be left between the segments
        gapRatio: 0.2,
        }],
}, '#element');

```

{% endtab %}

## Explode

Points can be exploded on mouse click by setting the `explode` property to true. You can also explode the point
on load using `explodeIndex`. Explode distance can be set by using `explodeOffset` property.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, PyramidSeries, IAccPointRenderEventArgs } from '@syncfusion/ej2-charts';
import { pyramidData } from './datasource.ts';
AccumulationChart.Inject(PyramidSeries);
let pyramidchart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: pyramidData,
        xName: 'x', yName: 'y',

        explode: true,

        //Specifies the distance of the point from the center during explode, which takes values in both pixels and percentage
        explodeOffset: '10',

        //If set true, all the points in the series will get exploded on load
        explodeAll: false,

        //Specifies index of the point, to be exploded on load
        explodeIndex:2

        }]
});
pyramidchart.appendTo('#element')

```

{% endtab %}

## Customization

Individual points can be customized using the `pointRender` event.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, PyramidSeries, IAccPointRenderEventArgs } from '@syncfusion/ej2-charts';
import { pyramidData } from './datasource.ts';
AccumulationChart.Inject(PyramidSeries);
let pyramidchart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Pyramid',
        dataSource: pyramidData,
        xName: 'x', yName: 'y',
        gapRatio: 0.04}],

    pointRender: (args: IAccPointRenderEventArgs) => {
        if ((args.point.x as string).indexOf('India') > -1) {
            args.fill = '#f4bc42';
        }
        else {
            args.fill = '#597cf9';
        }
    },
}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-label/)
* [Grouping](./grouping/)
