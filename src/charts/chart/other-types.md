---
title: " Chart Other Types | TypeScript "

component: "Chart"

description: "Chart contains box and wishker, errorbar, waterfall and histogram charts and also supports different customization"
---
<!-- markdownlint-disable MD036 -->

# Box and whisker

To render a box and whisker chart, use series [`type`](../api/chart/seriesModel/#type-string) as `BoxAndWhisker` and inject
`BoxAndWhiskerSeries` module using `Chart.Inject(BoxAndWhiskerSeries)` method. The field y requires n number of data or it should contains minimum of five values to plot a segment.

{% tab template= "chart/chart-types", es5Template="es5BoxAndWhisker" %}

```typescript
import {
    Chart, Category, ILoadedEventArgs,
    IPointRenderEventArgs, BoxAndWhiskerSeries, Tooltip, getElement, BoxPlotMode
} from '@syncfusion/ej2-charts';
Chart.Inject(Category, BoxAndWhiskerSeries, Tooltip);

let chart: Chart = new Chart({
    //Initializing Primary X Axis
    primaryXAxis: {
        valueType: 'Category',
    },
    //Initializing Chart Series
    series: [
        {
            type: 'BoxAndWhisker',
            dataSource: [
                { x: 'Development', y: [22, 22, 23, 25, 25, 25, 26, 27, 27, 28, 28, 29, 30, 32, 34, 32, 34, 36, 35, 38] },
                { x: 'Testing', y: [22, 33, 23, 25, 26, 28, 29, 30, 34, 33, 32, 31, 50] },
                { x: 'HR', y: [22, 24, 25, 30, 32, 34, 36, 38, 39, 41, 35, 36, 40, 56] },
                { x: 'Finance', y: [26, 27, 28, 30, 32, 34, 35, 37, 35, 37, 45] },
                { x: 'R&D', y: [26, 27, 29, 32, 34, 35, 36, 37, 38, 39, 41, 43, 58] },
                { x: 'Sales', y: [27, 26, 28, 29, 29, 29, 32, 35, 32, 38, 53] },
                { x: 'Inventory', y: [21, 23, 24, 25, 26, 27, 28, 30, 34, 36, 38] },
                { x: 'Graphics', y: [26, 28, 29, 30, 32, 33, 35, 36, 52] },
                { x: 'Training', y: [28, 29, 30, 31, 32, 34, 35, 36] }
            ],
            xName: 'x',
            yName: 'y',
            marker: {
                visible: true,
                width: 10,
                height: 10
            },
        }
    ],
}, '#element');

```

{%endtab%}

## Customization of Box and Whisker series

### boxPlotMode

You can change the rendering mode of the Box and Whisker series using the `boxPlotMode` property.
The default boxPlotMode is `exclusive`.The other boxPlotMode available are `inclusive` and `normal`.

{% tab template= "chart/chart-types", es5Template="es5BoxPlotMode" %}

```typescript
import {
    Chart, Category, IPointRenderEventArgs, BoxAndWhiskerSeries, Tooltip, getElement, BoxPlotMode
} from '@syncfusion/ej2-charts';
import { boxPlot } from './datasource.ts';
Chart.Inject(Category, BoxAndWhiskerSeries, Tooltip);

let chart: Chart = new Chart({
    //Initializing Primary X Axis
    primaryXAxis: {
        valueType: 'Category',
    },
    //Initializing Chart Series
    series: [
        {
            type: 'BoxAndWhisker',
            boxPlotMode: 'Normal',
            dataSource: boxPlot,
            xName: 'x',
            yName: 'y',
            marker: {
                visible: true,
                width: 10,
                height: 10
            },
        }],
}, '#element');

```

{%endtab%}

### showMean

In Box and Whisker series `showMean` property is used to show the box and whisker average value. The default value of `showMean` is false.

{% tab template= "chart/chart-types", es5Template="es5ShowMean" %}

```typescript
import {
    Chart, Category, ILoadedEventArgs,
    IPointRenderEventArgs, BoxAndWhiskerSeries, Tooltip, getElement, BoxPlotMode
} from '@syncfusion/ej2-charts';
import { boxPlot } from './datasource.ts';
Chart.Inject(Category, BoxAndWhiskerSeries, Tooltip);

let chart: Chart = new Chart({
    //Initializing Primary X Axis
    primaryXAxis: {
        valueType: 'Category',
    },
    //Initializing Chart Series
    series: [
        {
            type: 'BoxAndWhisker',
            dataSource: boxPlot,
            showMean: false,
            xName: 'x',
            yName: 'y',
        }
    ],
}, '#element');

```

{%endtab%}

## Waterfall Chart

Waterfall chart helps to understand the cumulative effect of the sequentially introduced positive
and negative values. To render a Waterfall series, use series [`type`](../api/chart/seriesModel/#type-string)
as `Waterfall` and inject `WaterfallSeries` module using `Chart.Inject(WaterfallSeries)` method.
[`intermediateSumIndexes`](../api/chart/seriesModel/#type-string) property of waterfall is used to represent
the in between sum values and [`sumIndexes`](../api/chart/seriesModel/#type-string)
is used to represent the cumulative sum values.

{% tab template= "chart/chart-types", es5Template="es5WaterFall" %}

```typescript

import { Chart, WaterfallSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(WaterfallSeries, Category, DataLabel);
let chartData: any[] = [
    { x: 'Income', y: 4711 }, { x: 'Sales', y: -1015 },
    { x: 'Development', y: -688 },
    { x: 'Revenue', y: 1030 }, { x: 'Balance' },
    { x: 'Administrative', y: -780 },
    { x: 'Expense', y: -361 }, { x: 'Tax', y: -695 },
    { x: 'Net Profit' }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series: [
        {
            dataSource: chartData,
            xName: 'x', yName: 'y', intermediateSumIndexes: [4], sumIndexes: [8],
            //Series type as Waterfall
            type: 'Waterfall',
        }
    ],
}, '#element');

```

{% endtab %}

**Customization of Waterfall Series**

The negative changes of waterfall series is
represented by using [`negativeFillColor`](../api/chart/seriesModel/#fill-string) and the summary changes are
represented by using [`summaryFillColor`](../api/chart/borderModel/) properties.

By default, the negativeFillColor as ‘#E94649’ and the summaryFillColor as ‘#4E81BC’.

{% tab template= "chart/chart-types", es5Template="es5WaterFallCust" %}

```typescript

import { Chart, WaterfallSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(WaterfallSeries, Category, DataLabel);

let chartData: any[] = [
    { x: 'Income', y: 4711 }, { x: 'Sales', y: -1015 },
    { x: 'Development', y: -688 },
    { x: 'Revenue', y: 1030 }, { x: 'Balance' },
    { x: 'Administrative', y: -780 },
    { x: 'Expense', y: -361 }, { x: 'Tax', y: -695 },
    { x: 'Net Profit' }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        labelFormat: '${value}M',
        minimum: 0, maximum: 5500, interval: 500,
    },
    series: [
        {
            dataSource: chartData,
            xName: 'x', yName: 'y', intermediateSumIndexes: [4], sumIndexes: [8],
            //Series type as Waterfall
            type: 'Waterfall',
            summaryFillColor: '#e56590', negativeFillColor: '#f8b883',
            marker: { dataLabel: { visible: true, position: 'Outer' } }
        }
    ],
}, '#element');

```

{% endtab %}

## Histogram Series

Histogram type charts can provide a visual display of large amounts of data that are difficult to understand in a tabular or spreadsheet form. To render a histogram chart, use series `type` as `Histogram`and inject `HistogramSeries` module using `Chart.Inject(HistogramSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Histogram" %}

```typescript

import {  Chart, HistogramSeries, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(HistogramSeries, DataLabel);

let chartData: Object[] = [];
let points: number[] = [5.250, 7.750, 0, 8.275, 9.750, 7.750, 8.275, 6.250, 5.750,
        5.250, 23.000, 26.500, 27.750, 25.025, 26.500, 26.500, 28.025, 29.250, 26.750, 27.250,
        26.250, 25.250, 34.500, 25.625, 25.500, 26.625, 36.275, 36.250, 26.875, 40.000, 43.000,
        46.500, 47.750, 45.025, 56.500, 56.500, 58.025, 59.250, 56.750, 57.250,
        46.250, 55.250, 44.500, 45.525, 55.500, 46.625, 46.275, 56.250, 46.875, 43.000,
        46.250, 55.250, 44.500, 45.425, 55.500, 56.625, 46.275, 56.250, 46.875, 43.000,
        46.250, 55.250, 44.500, 45.425, 55.500, 46.625, 56.275, 46.250, 56.875, 41.000, 63.000,
        66.500, 67.750, 65.025, 66.500, 76.500, 78.025, 79.250, 76.750, 77.250,
        66.250, 75.250, 74.500, 65.625, 75.500, 76.625, 76.275, 66.250, 66.875, 80.000, 85.250,
        87.750, 89.000, 88.275, 89.750, 97.750, 98.275, 96.250, 95.750, 95.250
    ];
points.map((value: number) => {
    chartData.push({
        y: value
    });
});
let chart: Chart = new Chart({
    primaryXAxis: {
        minimum: 0, maximum: 100
    },
    legendSettings: { visible: false },
    primaryYAxis: {
        minimum: 0, maximum: 50, interval: 10,
    },
    //Initializing Chart Series
    series: [
        {
            type: 'Histogram', width: 2, yName: 'y', name: 'Score',
            dataSource: chartData, binInterval: 20,
            showNormalDistribution: true, columnWidth: 0.99
        }
    ],
}, '#element');

```

{% endtab %}

## Error Bar Chart

Error bars are graphical representations of the variability of data and used on graphs to indicate the error or uncertainty in a reported
measurement. To render the error bar for the series, set [`visible`](../api/chart/seriesModel/#type-string)
as `true` and inject `ErrorBar` module using `Chart.Inject(ErrorBar)` method.

{% tab template= "chart/chart-types", es5Template="es5ErrorBar" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, ErrorBar);

let chartData: any[] = [{ x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 }, { x: 2008, y: 27 },
    { x: 2009, y: 32 }, { x: 2010, y: 35 }, { x: 2011, y: 30 }];
let chart: Chart = new Chart({
    series: [{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        errorBar: {
            visible: true,
        },
        type: 'Line'
    }],
}, '#element');

```

{% endtab %}

**Error Bar Type**

To change the error bar rendering type using [`type`](../api/chart/errorBarSettings/#type-string)
option of error bar. To change the error bar line length you can use [`verticalError`](../api/chart/errorBarSettings/#verticalError-number)
property.

{% tab template= "chart/chart-types", es5Template="es5ErrorBarType" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, ErrorBar);

let chart: Chart = new Chart({
    series: [{
        dataSource: numData,
        xName: 'x', yName: 'y',
        errorBar: {
            visible: true,
            type: 'Percentage',
            verticalError:4
        },
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

***Custom Error Bar***

To customize the error bar type, set error bar [`type`](../api/chart/errorBarSettings/#type-string) as `Custom` and
then change the horizontal/vertical positive and negative error of error bar.

{% tab template= "chart/chart-types", es5Template="es5ErrorBarCust" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, ErrorBar);

let chart: Chart = new Chart({
   series: [{
        dataSource: numData,
        xName: 'x', yName: 'y',
        errorBar: {
            visible: true,
            type: 'Custom',
            mode:'Both'
            verticalPostiveError:3,
            horizontalPositiveError:2,
            verticalNegativeError:3,
            horizontalNegativeError:2
        },
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Changing Error Bar Mode**

Error bar mode is used to define whether the error bar line has to be drawn horizontally, vertically or in both side.
To change the error bar mode use [`mode`](../api/chart/errorBarSettings/#mode-string) option.

{% tab template= "chart/chart-types", es5Template="es5ErrorBarMode" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, ErrorBar);

let chart: Chart = new Chart({
    series: [{
        dataSource: numData,
        xName: 'x', yName: 'y',
        errorBar: {
            visible: true,
            mode: 'Horizontal'
        },
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Changing Error Bar Direction**

To change the error bar direction to plus, minus or both side using [`direction`](../api/chart/errorBarSettings/#direction-string) option.

{% tab template= "chart/chart-types", es5Template="es5ErrorbarDirection" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, ErrorBar);

let chart: Chart = new Chart({
    series: [{
        dataSource: numData,
        xName: 'x', yName: 'y',
        errorBar: {
           visible: true,
           mode:'Vertical',
           direction:'Minus'
        },
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Customizing Error Bar Cap**

To customize the error bar cap length, width and fill color, you can use [`errorBarCap`](../api/chart/errorBarCapSettingsModel/) option.

{% tab template= "chart/chart-types", es5Template="es5ErrorBarCap" %}

```typescript

import { Chart, LineSeries, ErrorBar } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, ErrorBar);

let chart: Chart = new Chart({
    series: [{
        dataSource: numData,
        xName: 'x', yName: 'y',
        errorBar: {
            visible: true,
            errorBarCap:{
                length:10,
                width:10,
                color:'#0000ff'
            }
        },
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Vertical chart

In EJ2 chart, you can draw a chart in vertical manner by changing orientation of the axis. All series types support this feature.
You can use `isTransposed` property in chart to render a chart in vertical manner.

{% tab template= "chart/chart-types", es5Template="es5VerticalChart" %}

```typescript

import { Chart, SplineSeries, Category } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(SplineSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
       valueType: 'Category'
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Spline',
    }],
    isTransposed: true,

}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)
