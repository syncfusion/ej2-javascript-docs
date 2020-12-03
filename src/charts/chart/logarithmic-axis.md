---
title: " Chart Logarithmic Axis | TypeScript "

component: "Chart"

description: "Logarithmic axis uses logarithmic scale is defined as one where the units on an axis are powers, or logarithms, of a base number, usually 10."
---

# Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic axis uses logarithmic scale and it is very useful in visualizing data, when it has numerical values in
both lower order of magnitude (eg: 10<sup>-6</sup>) and higher order of magnitude (eg: 10<sup>6</sup>).

{% tab template= "chart/axis", es5Template="es5LogAxis" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Logarithmic);
let chartData: any[] = [{ x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
    { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
    { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
    { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
    { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
    { x: new Date(2005, 0, 1), y: 11000 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
    },
    primaryYAxis: {
        // Logarithmic scale in primary X Axis
        valueType: 'Logarithmic',
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

>Note: To use log axis, we need to inject `Logarithmic` using method `Chart.Inject(Logarithmic)` and
set the [`valueType`](../api/chart/axis/#valuetype-string) of axis to `Logarithmic`.

## Range

Range of an axis, will be calculated automatically based on the provided data, you can also customize the range of an axis using [`minimum`](../api/chart/axis/#minimum-object),[`maximum`](../api/chart/axis/#maximum-object)
and [`interval`](../api/chart/axis/#interval-number) property of the axis.

{% tab template= "chart/axis", es5Template="es5LogRange" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
import { logData } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Logarithmic);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
    },
    primaryYAxis: {
        //Logarithmic scale range in primary X Axis
        valueType: 'Logarithmic',
        minimum: 100,
        maximum: 10000
    },
    series:[{
        dataSource: logData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Logarithmic Base

Logarithmic base can be customized by using the [`logBase`](../api/chart/axis/#logbase-number) property of the axis.
For example when the logBase is 5, the axis values follows 5<sup>-2</sup>, 5<sup>-1</sup>, 5<sup>0</sup>,
5<sup>1</sup>, 5<sup>2</sup> etc.

{% tab template= "chart/axis", es5Template="es5LogBase" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
import { logData } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Logarithmic);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
    },
    primaryYAxis: {
        valueType: 'Logarithmic',
        // logBase for logarithmic scale
        logBase: 2
    },
    series:[{
        dataSource: logData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Logarithmic Interval

Logarithmic axis interval can be customized by using the [`interval`](../api/chart/axis/#interval-number)
property of the axis. When the logarithmic base is 10 and logarithmic interval is 2, then the axis labels
are placed at an interval of 10<sup>2</sup>. The default value of the interval is 1.

{% tab template= "chart/axis", es5Template="es5LogInterval" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
import { logData } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Logarithmic);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
    },
    primaryYAxis: {
        //Logarithmic interval in primary X Axis
        valueType: 'Logarithmic',
        interval: 2
    },
    series:[{
        dataSource: logData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}
