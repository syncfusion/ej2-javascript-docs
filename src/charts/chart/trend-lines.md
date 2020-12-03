---
title: " Chart Trendlines | TypeScript "

component: "Chart"

description: "Trendlines are used to show the direction and speed of price. Chart supports 6 types of trendlines and also provides trendlines customization."
---
<!-- markdownlint-disable MD036 -->

# Trendlines

Trendlines are used to show the direction and speed of price.

Trendlines can be generated for Cartesian type series (Line, Column, Scatter, Area, Candle, Hilo etc.) except bar type series. You can add more than one trendline to a series.

Chart supports 6 types of trendlines.

## Linear

A linear trendline is a best fit straight line that is used with simpler data sets. To render a linear trendline,
use trendline [`type`](../api/chart/trendlineModel/) as `Linear` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

{% tab template= "chart/trendlines", es5Template="es5LinearTrendline" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, Tooltip, LineSeries, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Tooltip, Trendlines Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'Linear' }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Exponential

An exponential trendline is a curved line that is most useful when data values rise or fall at increasingly higher rates. You cannot create an exponential trendline, if your data contains zero or negative values.

To render a exponential trendline,
use trendline [`type`](../api/chart/trendlineModel/) as `Exponential` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

{% tab template= "chart/trendlines", es5Template="es5ExpoTrendline" %}

```typescript

import { Chart, ScatterSeries,Trendlines, SplineSeries, Category, LineSeries, Tooltip, Crosshair, Legend, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(ScatterSeries, LineSeries, SplineSeries, Category, Tooltip, Crosshair, Trendlines, Legend, DateTime);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}

let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        type: 'Scatter',
        trendlines: [
            { type: 'Exponential',enableTooltip:true,marker:{visible:true} }
            ]
            }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Logarithmic

A logarithmic trendline is a best-fit curved line that is most useful when the rate of change in the data increases or decreases quickly and then levels out. A logarithmic trendline can use negative and/or positive values.

To render a logarithmic trendline, use trendline [`type`](../api/chart/trendlineModel/) as `Logarithmic` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

{% tab template= "chart/trendlines", es5Template="es5LogTrendline" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, LineSeries,Tooltip, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'Logarithmic' }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Polynomial

A polynomial trendline is a curved line that is used when data fluctuates.

To render a polynomial trendline,
use trendline [`type`](../api/chart/trendlineModel/) as `Polynomial` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

`polynomialOrder` used to define the polynomial value.

{% tab template= "chart/trendlines", es5Template="es5PolyTrendline" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, LineSeries, Tooltip, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'Polynomial' }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Power

A power trendline is a curved line that is best used with data sets that compare measurements that increase at a specific rate.

To render a power trendline, use trendline [`type`](../api/chart/trendlineModel/) as `Power` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

{% tab template= "chart/trendlines", es5Template="es5PowerTrendline" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, LineSeries, Tooltip, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let powerData: any[] = [
    { x: 1, y: 10 }, { x: 2, y: 50 },{ x: 3, y: 80 }, { x: 4, y: 110 },
    { x: 5, y: 180 }, { x: 6, y: 220 }, { x: 7, y: 300 }, { x: 8, y: 370 }, { x: 9, y: 490 }, { x: 10, y: 500 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 50
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: powerData,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'Power' }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Moving Average

A moving average trendline smoothen out fluctuations in data to show a pattern or trend more clearly.

To render a moving average trendline, use trendline [`type`](../api/chart/trendlineModel/) as `MovingAverage` and inject
`Trendlines` module using `Chart.Inject(Trendlines)`.

`period` property defines the period to find the moving average.

{% tab template= "chart/trendlines", es5Template="es5MovingAverage" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, LineSeries, Tooltip, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'MovingAverage' }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

**Customization of Trendline**

The [`fill`](../api/chart/trendlineModel/#fill-string) and [`width`](../api/chart/trendlineModel/#width-number) properties are used to customize the appearance of the trendline.

{% tab template= "chart/trendlines", es5Template="es5TrendlineCust" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, Tooltip, LineSeries, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',

        trendlines: [{ type: 'MovingAverage', fill: 'red', width:2 }]
    }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

## Forecasting

Trendline forecasting is the prediction of future/past situations.

Forward Forecasting and Backward Forecasting are the two types of forecasting.

**Forward Forecasting**

The value set for forwardForecast is used to determine the distance moving towards the future trend.

{% tab template= "chart/trendlines", es5Template="es5Forecast" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, Tooltip, LineSeries, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',
        trendlines: [{
            type: 'Linear',
            //forward forecast value
            forwardForecast:5
            }]
        }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}

**Backward Forecasting**

The value set for the backwardForecast is used to determine the past trends.

{% tab template= "chart/trendlines", es5Template="es5BackForecast" %}

```typescript

import {  Chart, Category, Trendlines, ScatterSeries, SplineSeries, LineSeries, Tooltip, TrendlineTypes} from '@syncfusion/ej2-charts';
Chart.Inject(Chart, ScatterSeries, SplineSeries, LineSeries, Trendlines, Tooltip, Category);

let data: Object[] = [];
let yValue: number[] = [7.66, 8.03, 8.41, 8.97, 8.77, 8.20, 8.16, 7.89, 8.68, 9.48, 10.11, 11.36, 12.34, 12.60, 12.95, 13.91, 16.21, 17.50, 22.72, 28.14, 31.26, 31.39, 32.43, 35.52, 36.36,
    41.33, 43.12, 45.00, 47.23, 48.62, 46.60, 45.28, 44.01, 45.17, 41.20, 43.41, 48.32, 45.65, 46.61, 53.34, 58.53];
let point: Object;
let i: number; let j: number = 0;
for (i = 1973; i <= 2013; i++) {
    point = { x: i, y: yValue[j] };
    data.push(point);
    j++;
}
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
    },
    primaryYAxis: {
        title: 'Rupees against Dollars',
        interval: 5
    },
    tooltip:{enable:true},
    chartArea: { border: { width: 0 } },
    series: [{
        dataSource: data,
        xName: 'x', yName: 'y',
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as scatter
        type: 'Scatter',
        trendlines: [{
                type: 'Linear',
                //backward forecast value
                backwardForecast: 5
                }]
        }],

    title: 'Historical Indian Rupee Rate (INR USD)'
}, '#element');

```

{% endtab %}