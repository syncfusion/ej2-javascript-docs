---
title: " Chart Data Editing | Typescript "
component: "Chart"
description: "Data editing is one of the user interaction feature. It provides the chart data that to change their value by using mouse cursor."
---

<!-- markdownlint-disable MD036 -->

# Data Editing

## Enable Data Editing

We can use the data editing through inject the `DataEditing` module in the chart. It provides drag and drop support to the rendered points. Now, we can change the location or value of the point based on its `y` value.  To enable the data editing, set the `enable` property to true in the drag settings of the series. Also, we can set color using `fill` property and set the data editing minimum and maximum range using `minY` and `maxY` properties.

{% tab template= "chart/user-interaction", es5Template="es5DataEditing" %}

```typescript

import { Chart, ColumnSeries, DateTime, Legend, LineSeries, Tooltip, DataEditing } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DateTime, Legend, LineSeries, Tooltip, DataEditing);

let chart: Chart = new Chart({

     primaryXAxis: {
        valueType: 'DateTime',
        labelFormat: 'y',
        intervalType: 'Years',
        edgeLabelPlacement: 'Shift',
        majorGridLines: { width: 0 }
    },
    //Initializing Primary Y Axis
    primaryYAxis:
    {
        labelFormat: '{value}%',
        rangePadding: 'None',
        minimum: 0,
        maximum: 100,
        interval: 20,
        lineStyle: { width: 0 },
        majorTickLines: { width: 0 },
        minorTickLines: { width: 0 }
    },
    chartArea: {
        border: {
            width: 0
        }
    },
    //Initializing Chart Series
    series: [
        {
            type: 'Column',
            dataSource: [
                { x: new Date(2005, 0, 1), y: 21 }, { x: new Date(2006, 0, 1), y: 24 },
                { x: new Date(2007, 0, 1), y: 36 }, { x: new Date(2008, 0, 1), y: 38 },
                { x: new Date(2009, 0, 1), y: 54 }, { x: new Date(2010, 0, 1), y: 57 },
                { x: new Date(2011, 0, 1), y: 70 }
            ],
            xName: 'x', width: 2, marker: {
                visible: true,
                width: 10,
                height: 10
            },
            yName: 'y', name: 'Germany', dragSettings: { enable: true, }
        },
        {
            type: 'Line',
            dataSource: [
                { x: new Date(2005, 0, 1), y: 21 }, { x: new Date(2006, 0, 1), y: 24 },
                { x: new Date(2007, 0, 1), y: 36 }, { x: new Date(2008, 0, 1), y: 38 },
                { x: new Date(2009, 0, 1), y: 54 }, { x: new Date(2010, 0, 1), y: 57 },
                { x: new Date(2011, 0, 1), y: 70 }
            ],
            xName: 'x', width: 2, marker: {
                visible: true,
                width: 10,
                height: 10
            },
            yName: 'y', name: 'Germany', dragSettings: { enable: true, }
        }
    ],

    //Initializing Chart title
    title: 'Inflation - Consumer Price',
    //Initializing User Interaction Tooltip
    tooltip: {
        enable: true
    },
}, '#element');

```

{% endtab %}