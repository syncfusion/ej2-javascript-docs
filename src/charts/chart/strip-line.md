---
title: " Chart Strip-lines | TypeScript "

component: "Chart"

description: "Strip Lines are vertical or horizontal lines used to highlight/mark a certain region on the plot area."
---
<!-- markdownlint-disable MD036 -->

# Strip lines

<!-- markdownlint-disable MD036 -->

EJ2 chart supports horizontal and vertical strip lines and customization of stripline in both orientation.
To use strip line in axis, we need to inject `StripLine` module using `Chart.Inject(StripLine)` method

## Horizontal Strip lines

You can create Horizontal stripline by adding the `stripline` in the vertical axis and set `visible` option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis", es5Template="es5StripLinesHorizontal" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries, DataLabel, StripLine);
let chartData: any[] = [{x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
   {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7}];
let chart: Chart = new Chart({
   primaryYAxis: {
       stripLines:[
            { start: 15, end: 22 },
            { start: 8, end: 15 },
            { start: 0, end: 8 }]
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', type: 'Column'
        }],
}, '#element');

```

{% endtab %}

## Vertical Striplines

You can create vertical stripline by adding the`stripline` in the horizontal axis and set `visible` option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis", es5Template="es5StripLinesVertical" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
import { stripData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, LineSeries, DataLabel, StripLine);

let chart: Chart = new Chart({
    primaryXAxis: {
        stripLines:[
            {start: 0, end: 5 },
            {start: 5, end: 10 },
        ]
    },
   series:[{
        dataSource: stripData,
        xName: 'x', yName: 'y',
        type: 'Column'}],
},'#element');

```

{% endtab %}

## Customize the strip line

Starting value in specific strip line can be customized by `start` property in strip line. Similarly, ending value is customized by `end`. It can be also set for starting from the corresponding origin of the axis by
`startFromOrigin`. Size of the strip line is customized by `size`. Border for the stripline is customized by `border`. Order of the strip line such that whether it should be rendered in behind or over the series elements
is customized by `zIndex`.

{% tab template= "chart/axis", es5Template="es5StripLineCus" %}

```typescript

import { Chart, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
import { stripData } from './datasource.ts';
Chart.Inject(ColumnSeries, LineSeries, DataLabel, StripLine);

let chart: Chart = new Chart({
    primaryXAxis: {
        stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5}
        ]
    },
    series:[{
        dataSource: stripData,
        xName: 'x', yName: 'y',
        type: 'Column',
}]
}, '#element');

```

{% endtab %}

## Customize the stripline text

You can customize the text rendered in stripline by `textStyle` property. Rotation of the strip line text can be changed by `rotation` property.
Horizontal and Vertical alignment of stripline text can be changed by `horizontalAlignment` and `verticalAlignment` property.

{% tab template= "chart/axis", es5Template="es5StripLineText" %}

```typescript

import { Chart, ColumnSeries, LineSeries, StripLine } from '@syncfusion/ej2-charts';
import { stripData } from './datasource.ts';
Chart.Inject(ColumnSeries, LineSeries, StripLine);

let chart: Chart = new Chart({
    primaryXAxis: {
        stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5,  text: 'Good', verticalAlignment: 'Middle', horizontalAlignment: 'Middle', rotation: 90, textStyle: { size: 15}},
            { start: 5, end: 8, verticalAlignment: 'Start', horizontalAlignment: 'End', rotation: 45, text: 'Poor'}
        ]
    },
   series:[{
        dataSource: stripData,
        xName: 'x', yName: 'y',
        type: 'Column',
     }],
},'#element');

```

{% endtab %}

## See Also

* [Mark the threshold in chart](./how-to/#mark-a-threshold-in-chart)