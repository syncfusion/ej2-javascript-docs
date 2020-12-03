---
title: " Chart Axis Labels | TypeScript "

component: "Chart"

description: "Chart contains smart axis labels, label positioning, multilevelabels, text customization and sorting properties "
---

# Axis Labels

## Smart Axis Labels

When the axis labels overlap with each other, you can use
[`labelIntersectAction`](../api/chart/axis/) property in the axis,
to place them smartly.

When setting `labelIntersectAction` as `Hide`

{% tab template= "chart/axis", es5Template="es5SmartAxis" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [{ x: "South Korea", y: 39.4 }, { x: "India", y: 61.3 }, { x: "Pakistan", y: 20.4 },
    { x: "Germany", y: 65.1 }, { x: "Australia", y: 15.8 }, { x: "Italy", y: 29.2 },
    { x: "United Kingdom", y: 44.6 }, { x: "Saudi Arabia", y: 9.7 }, { x: "Russia", y: 40.8 },
    { x: "Mexico", y: 31 }, { x: "Brazil", y: 75.9 }, { x: "China", y: 51.4 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        //label intersect as hide
        labelIntersectAction: 'Hide'
    },
   series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

When setting `labelIntersectAction` as `Rotate45`

{% tab template= "chart/axis", es5Template="es5labelIntersect" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
import { smartAxisData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        // label intersect as 45
        labelIntersectAction: 'Rotate45'
    },
   series:[{
        dataSource: smartAxisData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

When setting `labelIntersectAction` as `Rotate90`

{% tab template= "chart/axis", es5Template="es5LabelIntersect45" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
import { smartAxisData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        // label intersect as 90
        labelIntersectAction: 'Rotate90'
    },
    series:[{
        dataSource: smartAxisData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Axis Labels Positioning

By default, the axis labels can be placed at `outside` the axis line and this also can be placed at `inside` the axis line using the `labelPosition` property.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        // label placement as on ticks
        labelPosition: 'Inside',
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Multilevel Labels

Any number of levels of labels can be added to an axis using the `multiLevelLabels` property. This property can be configured using the following properties:
• Categories
• Overflow
• Alignment
• Text style
• Border

>Note: To use multilevel label feature, we need to inject `MultiLevelLabel` using `Chart.Inject(MultiLevelLabel)` method.

### Categories

Using the categories property, you can configure the `start`, `end`, `text`, and `maximumTextWidth` of multilevel labels.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, MultiLevelLabel } from '@syncfusion/ej2-charts';
import { categoryData, MultiLevelLabel } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, MultiLevelLabel);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
           multiLevelLabels:[{ categories: [
                        {
                            //Start and end values of the multi-level labels accepts number, date and sring values
                            start: -0.5,
                            end: 3.5,
                            //Multi-level label's text.
                            text: 'Half Yearly 1',
                            //Maximum width of the text for multi level labes
                            maximumTextWidth:50
                        },
                        { start: 3.5, end: 7.5, text: 'Half Yearly 2',maximumTextWidth:50 },
                    ]}]
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

### Overflow

Using the `overflow` property, you can `trim` or `wrap` the multilevel labels.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, MultiLevelLabel } from '@syncfusion/ej2-charts';
import { categoryData, MultiLevelLabel } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, MultiLevelLabel);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
           multiLevelLabels:[{
               categories: [{start: -0.5, end: 3.5, text: 'Half Yearly 1', maximumTextWidth:50 },
                        { start: 3.5, end: 7.5, text: 'Half Yearly 2',maximumTextWidth:50 }],
               overflow:'Trim'
           }]
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

### Alignment

The `alignment` property provides option to position the multilevel labels at `far`, `center`, or `near`.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, MultiLevelLabel } from '@syncfusion/ej2-charts';
import { categoryData, MultiLevelLabel } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, MultiLevelLabel);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
           multiLevelLabels:[{
               categories: [{start: -0.5, end: 3.5, text: 'Half Yearly 1' },
                        { start: 3.5, end: 7.5, text: 'Half Yearly 2' }],
                alignment :'Far'
           }]
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

### Text customization

The `textStyle` property of multilevel labels provides options to customize the `size`, `color`, `fontFamily`, `fontWeight`, `fontStyle`, `opacity`, `textAlignment` and `textOverflow`.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, MultiLevelLabel } from '@syncfusion/ej2-charts';
import { categoryData, MultiLevelLabel } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, MultiLevelLabel);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
           multiLevelLabels:[{
               categories: [{start: -0.5, end: 3.5, text: 'Half Yearly 1' },
                        { start: 3.5, end: 7.5, text: 'Half Yearly 2' }],
               textStyle:{size:'18px', color:'Red'}
           }]
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

### Border customization

Using the `border` property, you can customize the `width`, `color`, and `type`. The `type` of border are `Rectangle`, `Brace`, `WithoutBorder`, `WithoutTopBorder`, `WithoutTopandBottomBorder` and `CurlyBrace`.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, MultiLevelLabel } from '@syncfusion/ej2-charts';
import { categoryData, MultiLevelLabel } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, MultiLevelLabel);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
           multiLevelLabels:[{
               categories: [{start: -0.5, end: 3.5, text: 'Half Yearly 1' },
                        { start: 3.5, end: 7.5, text: 'Half Yearly 2' }],
               border:{type:'Brace', color:'Blue', width: 2},
           }]
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Edge Label Placement

Labels with long text at the edges of an axis may appear partially in the chart. To avoid this,
use [`edgeLabelPlacement`](../api/chart/axis/) property in axis, which
moves the label inside the chart area for better appearance or hides it.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        //Edgelabelplacement for primary x axis
        edgeLabelPlacement: 'Shift',
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Sorting

The chart’s data source can be sorted using the `sort` method of chart. The arguments that are required to pass to sort method are data of chart. The fields depend on which sorting is performed either `x` or `y`, and the `isDescending` with which data source values are sorted in either `ascending` or `descending`.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        //Edgelabelplacement for primary x axis
        edgeLabelPlacement: 'Shift',
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Labels Customization

Border of the axis labels can be customized using `width`, `color` and `typr` property of the axis.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        border: { width: 1, type: 'Rectangle' , color: 'red'}
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Customizing Specific Point

You can customize the specific text in the axis labels using `axisLabelRender` event.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category, IAxisLabelRenderEventArgs } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        border: { width: 1, type: 'Rectangle' , color: 'red'}
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],
    axisLabelRender : (args : IAxisLabelRenderEventArgs ) => {
        if(args.text === 'France') {
            args.labelStyle.color = 'Red';
        }
    }

}, '#element');

```

{% endtab %}

## Line break support

Line break feature used to customize the long axis label text into multiple lines by using tag. Refer the below example in that dataSource x value contains long text, it breaks into two lines by using  `<br>` tag.

{% tab template= "chart/axis", es5Template="es5LineBreak" %}

```typescript

import {
    Chart, BarSeries, DataLabel, Category,
    Tooltip
} from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(BarSeries, Category, Tooltip, DataLabel);

    let chart: Chart = new Chart({
        //Initializing Primary X and YAxis
        primaryXAxis: {
            title: 'Country',
            valueType: 'Category',
            majorGridLines: { width: 0 },
            enableTrim: false,
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
            minimum: 0,
            maximum: 800,
            labelFormat: Browser.isDevice ? '{value}' : '{value}M',
            labelStyle: {
                color: 'transparent'
            }
        },
        chartArea: {
            border: {
                width: 0
            }
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Bar', tooltipMappingName: 'country',
                dataSource: [
                    { x: 'Germany', y: 72, country: 'GER: 72'},
                    { x: 'Russia', y: 103.1, country: 'RUS: 103.1'},
                    { x: 'Brazil', y: 139.1, country: 'BRZ: 139.1'},
                    { x: 'India', y: 462.1, country: 'IND: 462.1'},
                    { x: 'China', y: 721.4, country: 'CHN: 721.4'},
                    { x: 'United States<br>Of America', y: 286.9, country: 'USA: 286.9'},
                    { x: 'Great Britain', y: 115.1, country: 'GBR: 115.1'},
                    { x: 'Nigeria', y: 97.2, country: 'NGR: 97.2'},

                ],
                xName: 'x', width: 2,
                yName: 'y', marker: {
                    dataLabel: {
                        visible: true,
                        position: 'Top', font: {
                            fontWeight: '600',
                            color: '#ffffff'
                        }
                    }
                },
                name: 'Users'
            }
        ],
        legendSettings: {
            visible: false
        }
}, '#element');

```

{% endtab %}

## Maximum Labels

`MaximumLabels` property is set, then the labels will be rendered based on the count in the property per 100 pixel. If you have set range (minimum, maximum, interval) and maximumLabels, then the priority goes to range only. If you haven’t set the range, then we have considered priority to maximumLabels property.

{% tab template= "chart/axis", es5Template="es5MaximumLabel" %}

```typescript

import { DateTime, ILoadedEventArgs, ChartTheme, ScrollBar } from '@syncfusion/ej2-charts';
import { Chart, AreaSeries, Legend, Zoom } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom, ScrollBar);

    let series1: Object[] = [];
    let point1: Object;
    let value: number = 80;
    let i: number;
    for (i = 1; i < 50; i++) {
        if (Math.random() > .5) {
            value += Math.random();
        } else {
            value -= Math.random();
        }
        point1 = { x: i, y: value.toFixed(1) };
        series1.push(point1);
    }
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Years',
           edgeLabelPlacement: 'Shift',
            majorGridLines : { width : 0 },
           maximumLabels:1,
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Profit ($)',
            rangePadding: 'None',
            lineStyle : { width: 0 },
            majorTickLines : {width : 0}
        },
       chartArea : {border : {width : 0}},

        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                fill: 'url(#gradient-chart)',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableMouseWheelZooming: true,
            enablePinchZooming: true,
            enableSelectionZooming: true,
            mode: 'X',
            enableScrollbar: true
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
    },'#element');

```

{% endtab %}