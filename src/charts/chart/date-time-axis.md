---
title: " Chart Datetime Axis | TypeScript "

component: "Chart"

description: "Date time axis uses date time scale and displays the date time values as axis labels in the specified format."
---
<!-- markdownlint-disable MD036 -->

# DateTime and DateTimeCategory Axis

## DateTime Axis

Date time axis uses date time scale and displays the date time values as axis labels in the specified format.

{% tab template= "chart/axis", es5Template="es5DateTime" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [{ x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        // Date time scale in primary X Axis
        valueType: 'DateTime',
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

>Note: To use datetime axis, we need to inject DateTime using `Chart.Inject(DateTime)` method and
set the [`valueType`](../api/chart/axis/#valuetype-string) of axis to DateTime.

## DateTimeCategory Axis

Date-time category axis is used to display the date-time values with non-linear intervals. For example, the business days alone have been depicted in a week here.

{% tab template= "chart/axis", es5Template="es5DateTime" %}

```typescript

import { Chart, DateTimeCategory, ColumnSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DateTimeCategory);
let chartData: any[] = [{ x: new Date(2017, 11, 20), y: 21 }, { x: new Date(2017, 11, 21), y: 24 },
                    { x: new Date(2017, 11, 22), y: 24 }, { x: new Date(2017, 11, 26), y: 70 },
                    { x: new Date(2017, 11, 27), y: 75 }, { x: new Date(2018, 0, 2), y: 82 },
                    { x: new Date(2018, 0, 3), y: 53 }, { x: new Date(2018, 0, 4), y: 54 },
                    { x: new Date(2018, 0, 5), y: 53 }, { x: new Date(2018, 0, 8), y: 45 }
                ];
   let chart: Chart = new Chart({

        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'DateTimeCategory',
            skeleton: 'Ed',
        },
        series: [
            {
                type: 'Column',
                dataSource: chartData,
                xName: 'x', yName: 'y',
            },
        ],

}, '#element');

```

{% endtab %}

>Note: To use dateTimeCategory axis, we need to inject DateTimeCategory using `Chart.Inject(DateTimeCategory)` method and
set the [`valueType`](../api/chart/axis/#valuetype-string) of axis to DateTimeCategory.

### Range

Range of an axis will be calculated automatically based on the provided data, you can also customize the
range of the axis using [`minimum`](../api/chart/axis/#minimum-object),
[`maximum`](../api/chart/axis/#maximum-object) and [`interval`](../api/chart/axis/#interval-number) property
of the axis.

{% tab template= "chart/axis", es5Template="es5DateTimeRange" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        // Date time range in primary X Axis
        valueType: 'DateTime',
        minimum: new Date(2000, 6, 1),
        maximum: new Date(2010, 6, 1), interval: 1
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

### Interval Customization

Date time intervals can be customized by using the [`interval`](../api/chart/axis/#interval-number)
and [`intervalType`](../api/chart/axis/#intervaltype-string) properties of the axis.
For example, when you set interval as 2 and intervalType as years, it considers 2 years as interval.
Datetime axis supports following interval types,

* Auto
* Years
* Months
* Days
* Hours
* Minutes
* Seconds

{% tab template= "chart/axis", es5Template="es5DateTimeInterval" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        //interval type as years in primary x axis
        intervalType: 'Years'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Applying Padding to the Range**

Padding can be applied to the minimum and maximum extremes of the range by using the
[`rangePadding`](../api/chart/axis/#rangepadding-string) property. Date time axis supports the
following types of padding,

* None
* Round
* Additional

**Datetime - None**

When the [`rangePadding`](../api/chart/axis/#rangepadding-string) is set to `None`, minimum and maximum of an axis is based on the data.

{% tab template= "chart/axis", es5Template="es5DateTimeNone" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        //Range padding as none
        rangePadding: 'None'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Datetime - Round**

When the [`rangePadding`](../api/chart/axis/#rangepadding-string) is set to `Round`, minimum and maximum will
be rounded to the nearest possible value, which is divisible by interval. For example, when the minimum is
15th Jan, interval is 1 and the interval type is ‘month’, then the axis minimum will be Jan 1st.

{% tab template= "chart/axis", es5Template="es5DateTimeRound" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        //Range padding as round
        rangePadding: 'Round'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

**Datetime - Additional**

When the [`rangePadding`](../api/chart/axis/#rangepadding-string) is set to `Additional`, interval of an axis
will be padded to the minimum and maximum of the axis.

{% tab template= "chart/axis", es5Template="es5DateTimeAdditional" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        //Range padding as additional
        rangePadding: 'Additional'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

## Label Format

You can format and parse the date to all globalize format using [`labelFormat`](../api/chart/axis/#labelformat-string) property in an axis.

{% tab template= "chart/axis", es5Template="es5DateTimeFormat" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(LineSeries, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        //Label format as yMd
        labelFormat: 'yMd'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}

The following table describes the result of applying some common date time formats to the `labelFormat` property

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format Property Value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>EEEE</td>
<td>Monday</td>
<td>The Date is displayed in day format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>yMd</td>
<td>04/10/2000</td>
<td>The Date is displayed in month/date/year format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td> MMM </td>
<td>Apr</td>
<td>The Shorthand month for the date is displayed</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hm</td>
<td>12:00 AM</td>
<td>Time of the date value is displayed as label</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hms</td>
<td>12:00:00 AM</td>
<td>The Label is displayed in hours:minutes:seconds format</td>
</tr>
</table>

## Custom Label Format

Axis also supports custom label format using placeholder like {value}°C, in which the value represent the axis label e.g 20°C.

{% tab template= "chart/axis", es5Template="es5CustomFormat" %}

```typescript

import { Chart, DateTime, LineSeries} from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(DateTime, LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
         valueType: 'DateTime',
    },
    primaryYAxis: {
        // Custom label format
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: data,
        xName: 'x', yName: 'y',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}