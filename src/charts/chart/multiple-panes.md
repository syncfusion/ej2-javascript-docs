---
title: " Chart Multiple-panes | TypeScript "

component: "Chart"

description: "Chart can be divided multiple rows and columns. Axes are rendering based on row index or column index in pane."
---

# Multiple Panes

Chart area can be divided into multiple panes using [`rows`](../api/chart/row/) and [`columns`](../api/chart/column/).

## Rows

To split the chart area vertically into number of rows, use [`rows`](../api/chart/row/) property of the chart.

* You can allocate space for each row by using the [`height`](../api/chart/row/#height-string) property. The value can be either
 percentage or in pixel.
* To associate a vertical axis to a particular row, specify its index to
[`rowIndex`](../api/chart/axis/#rowindex-number) property of the axis.
* To customize each row’s bottom line, use  [`border`](../api/chart/row/#border-bordermodel) property.

{% tab template= "chart/axis", es5Template="es5MultipleRows" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: 'Jan', y: 15, y1: 33 }, { x: 'Feb', y: 20, y1: 31 }, { x: 'Mar', y: 35, y1: 30 },
    { x: 'Apr', y: 40, y1: 28 }, { x: 'May', y: 80, y1: 29 }, { x: 'Jun', y: 70, y1: 30 },
    { x: 'Jul', y: 65, y1: 33 }, { x: 'Aug', y: 55, y1: 32 }, { x: 'Sep', y: 50, y1: 34 },
    { x: 'Oct', y: 30, y1: 32 }, { x: 'Nov', y: 35, y1: 32 }, { x: 'Dec', y: 35, y1: 31 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'Category',
        interval: 1
    },
    primaryYAxis: {
        minimum: 0, maximum: 90, interval: 20,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F'
    },
    // Rows for chart axis
    rows:[
        {
            height: '50%'
        },{
            height: '50%'
        }
    ],
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 1, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 4,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Germany', type: 'Column'
    },{
        dataSource: chartData, width:2,
        xName: 'x', yName: 'y1', yAxisName: 'yAxis'
        name: 'Japan', type: 'Line',
        marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } }
    }],
    title: 'Weather Condition'
}, '#element');

```

{% endtab %}

For spanning the vertical axis along multiple row, you can use [`span`](../api/chart/axis/#span-number) property of an axis.

{% tab template= "chart/axis", es5Template="es5SpanAxis" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: 'Jan', y: 15, y1: 33 }, { x: 'Feb', y: 20, y1: 31 }, { x: 'Mar', y: 35, y1: 30 },
    { x: 'Apr', y: 40, y1: 28 }, { x: 'May', y: 80, y1: 29 }, { x: 'Jun', y: 70, y1: 30 },
    { x: 'Jul', y: 65, y1: 33 }, { x: 'Aug', y: 55, y1: 32 }, { x: 'Sep', y: 50, y1: 34 },
    { x: 'Oct', y: 30, y1: 32 }, { x: 'Nov', y: 35, y1: 32 }, { x: 'Dec', y: 35, y1: 31 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'Category',
        interval: 1
    },
    primaryYAxis: {
        minimum: 0, maximum: 90, interval: 10,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F',
        //Span for chart axis
        span: 2
    },
    rows:[
        {
            height: '50%'
        },{
            height: '50%'
        }
    ],
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 1, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 2,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Germany', type: 'Column'
    },{
        dataSource: chartData, width:2,
        xName: 'x', yName: 'y1', yAxisName: 'yAxis'
        name: 'Japan', type: 'Line',
        marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } }
    }],
    title: 'Weather Condition'
}, '#element');

```

{% endtab %}

## Columns

To split the chart area horizontally into number of columns, use [`columns`](../api/chart/column/) property of the chart.

* You can allocate space for each column by using the [`width`](../api/chart/row/#width-string) property. The given width can be either
 percentage or in pixel.
* To associate a horizontal axis to a particular column, specify its index to
[`columnIndex`](../api/chart/axis/#columnindex-number) property of the axis.
* To customize each column’s bottom line, use [[`border`](../api/chart/row/#border-bordermodel) property.

{% tab template= "chart/axis", es5Template="es5MultipleColumns" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: 'Jan', y: 15, y1: 33 }, { x: 'Feb', y: 20, y1: 31 }, { x: 'Mar', y: 35, y1: 30 },
    { x: 'Apr', y: 40, y1: 28 }, { x: 'May', y: 80, y1: 29 }, { x: 'Jun', y: 70, y1: 30 },
    { x: 'Jul', y: 65, y1: 33 }, { x: 'Aug', y: 55, y1: 32 }, { x: 'Sep', y: 50, y1: 34 },
    { x: 'Oct', y: 30, y1: 32 }, { x: 'Nov', y: 35, y1: 32 }, { x: 'Dec', y: 35, y1: 31 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        interval: 1
    },
    primaryYAxis: {
        minimum: 0, maximum: 90, interval: 10,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F'
    },
    // Columns for chart axis
    columns:[
        {
            width: '50%'
        },{
            width: '50%'
        }
    ],
    axes:[
        {
            majorGridLines: { width: 0 },
            columnIndex: 1,
            valueType: 'Category',
            lineStyle: { width: 0 },
            name: 'xAxis'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Germany', type: 'Column'
    },{
        dataSource: chartData, width:2,
        xName: 'x', yName: 'y1', xAxisName: 'xAxis'
        name: 'Japan', type: 'Line',
        marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } }
    }],
    title: 'Weather Condition'
}, '#element');

```

{% endtab %}

For spanning the vertical axis along multiple column, you can use [`span`](../api/chart/axis/#span-number)
property of an axis.

{% tab template= "chart/axis", es5Template="es5SpanVertical" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: 'Jan', y: 15, y1: 33 }, { x: 'Feb', y: 20, y1: 31 }, { x: 'Mar', y: 35, y1: 30 },
    { x: 'Apr', y: 40, y1: 28 }, { x: 'May', y: 80, y1: 29 }, { x: 'Jun', y: 70, y1: 30 },
    { x: 'Jul', y: 65, y1: 33 }, { x: 'Aug', y: 55, y1: 32 }, { x: 'Sep', y: 50, y1: 34 },
    { x: 'Oct', y: 30, y1: 32 }, { x: 'Nov', y: 35, y1: 32 }, { x: 'Dec', y: 35, y1: 31 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        interval: 1,
        // Span for chart axis
        span: 2
    },
    primaryYAxis: {
        minimum: 0, maximum: 90, interval: 10,
        lineStyle: { width: 0 },
        title: 'Temperature (Fahrenheit)',
        labelFormat: '{value}°F'
    },
    columns:[
        {
            width: '50%'
        },{
            width: '50%'
        }
    ],
    axes:[
        {
            valueType: 'Category',
            majorGridLines: { width: 0 },
            columnIndex: 1, opposedPosition: true,
            lineStyle: { width: 0 },
            name: 'xAxis'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Germany', type: 'Column'
    },{
        dataSource: chartData, width:2,
        xName: 'x', yName: 'y1', xAxisName: 'xAxis'
        name: 'Japan', type: 'Line',
        marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } }
    }],
    title: 'Weather Condition'
}, '#element');

```

{% endtab %}