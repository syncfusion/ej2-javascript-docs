---
title: " Chart Numeric Axis | TypeScript "

component: "Chart"

description: "Numeric axis used to represent numeric values data in chart. we can customize the range, label format and ranga padding in numeric axis. "
---
<!-- markdownlint-disable MD036 -->

# Numeric Axis

You can use [numeric axis](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-axis) to represent numeric values of data in chart. By default, the `valueType` of an axis is `Double`.

{% tab template= "chart/axis", es5Template="es5AxisDouble" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [{ x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 }, { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 }, { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 }, { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        // Numerical scale in primary X Axis
        valueType: 'Double',
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Range

Range of an axis, will be calculated automatically based on the provided data, you can also customize the
range of the axis using [`minimum`](../api/chart/axisModel/#minimum-object),
[`maximum`](../api/chart/axisModel/#maximum-object) and [`interval`](../api/chart/axisModel/#interval-number) property of
the axis.

{% tab template= "chart/axis", es5Template="es5DoubleRange" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        // Numeric axis range
        minimum: 1,
        maximum: 20,
        interval: 5
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Range Padding

Padding can be applied to the minimum and maximum extremes of an axis range by using the
[`rangePadding`](../api/chart/axisModel/#rangepadding-string) property. Numeric axis supports the following types of
padding.

* None
* Round
* Additional
* Normal
* Auto

**Numeric - None**

When the [`rangePadding`](../api/chart/axisModel/#rangepadding-string) is set to `None`, minimum and maximum of the axis is based on the data.

{% tab template= "chart/axis", es5Template="es5DoubleNone" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
    },
    primaryYAxis: {
        //RangePadding as none in Y Axis
        rangePadding: 'None'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Numeric - Round**

When the [`rangePadding`](../api/chart/axisModel/#rangepadding-string) is set to `Round`, minimum and maximum will
be rounded to the nearest possible value, which is divisible by interval. For example, when the minimum is 3.5 and
the interval is 1, then the minimum will be rounded to 3.

{% tab template= "chart/axis", es5Template="es5DoubleRound" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
     },
    primaryYAxis: {
        rangePadding: 'Round'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Numeric - Additional**

When the [`rangePadding`](../api/chart/axisModel/#rangepadding-string) is set to `Additional`, interval of an axis
will be added to the minimum and maximum of the axis.

{% tab template= "chart/axis", es5Template="es5DoubleAdditional" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
     },
    primaryYAxis: {
        rangePadding: 'Additional'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Numeric - Normal**

When the [`rangePadding`](../api/chart/axisModel/#rangepadding-string) is set to `Normal`, padding is applied to the axis based on default range calculation.

{% tab template= "chart/axis", es5Template= "es5DoubleNormal" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
    },
    primaryYAxis: {
        rangePadding: 'Normal'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Numeric - Auto**

When the [`rangePadding`](../api/chart/axisModel/#rangepadding-string) is set to `Auto`, horizontal numeric axis
takes None as padding calculation, while the vertical numeric axis takes Normal as padding calculation.

{% tab template= "chart/axis", es5Template="es5DoubleAuto" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        // Set the rangePadding as auto in X Axis
        rangePadding: 'Auto'
    },
    primaryYAxis: {
        valueType: 'Double',
        // Set the rangePadding as auto in Y Axis
        rangePadding: 'Auto'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Label Format

**Numeric Label Format**

Numeric labels can be formatted by using the [`labelFormat`](../api/chart/axisModel/#labelformat-string) property.
Numeric labels supports all globalize format.

{% tab template= "chart/axis", es5Template="es5LabelFormat" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(LineSeries);

let chart: Chart = new Chart({
    primaryYAxis: {
        //Label format as currency
        labelFormat: 'c'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

The following table describes the result of applying some commonly used label formats on numeric values.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

## GroupingSeparator

To separate groups of thousands, use [`useGroupingSeparator`](../api/chart/chartModel/#useGroupingSeparator-boolean) property in chart.

{% tab template= "chart/axis", es5Template="es5GroupingSep" %}

```typescript

import { Chart, ColumnSeries } from '@syncfusion/ej2-charts';
import { groupingData } from './datasource.ts';
Chart.Inject(ColumnSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: groupingData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],
useGroupingSeparator: true
}, '#element');

```

{% endtab %}

## Custom Label Format

Axis also supports custom label format using placeholder like {value}°C, in which the value represent the axis label e.g 20°C.

{% tab template= "chart/axis", es5Template="es5CustomFormat" %}

```typescript

import { Chart, ColumnSeries } from '@syncfusion/ej2-charts';
import { numericData } from './datasource.ts';
Chart.Inject(ColumnSeries);

let chart: Chart = new Chart({
    primaryYAxis: {
        // Custom label format
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: numericData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}