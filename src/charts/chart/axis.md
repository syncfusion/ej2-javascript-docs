
# Axis

Chart typically has two axis, which are used to measure and categorize data:
a horizontal or primary x axis and a vertical or primary y axis.

Vertical axis supports numerical and logarithmic scale. Horizontal axis supports the following types of scale.

* Category
* Numeric
* DateTime
* Logarithmic

In addition to this, both vertical and horizontal axis support inversed axis.

<!-- markdownlint-disable MD036 -->

## Category Axis

<!-- markdownlint-disable MD036 -->

Category axis are used to represent, the string values instead of numbers.

{% tab template= "chart/axis", es5Template="es5AxisCategory" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        //Category in primary X Axis
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Positioning Axis Labels**

By default, category labels are placed between the ticks in an axis, this can also be placed on ticks
using [`labelPlacement`](../api/chart/axis/#labelplacement) property.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        // label placement as on ticks
        labelPlacement: 'OnTicks',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

>Note: To use category axis, we need to inject `Category` module using `Chart.Inject(Category)` method and
set the [`valueType`](../api/chart/axis/#valuetype) of axis to Category.

## Numeric Axis

You can use numeric axis to represent numeric values of data in chart. By default, the `valueType` of an axis is `Double`.

{% tab template= "chart/axis", es5Template="es5AxisDouble" %}

```typescript

import { Chart, AreaSeries } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        // Numerical scale in primary X Axis
        valueType: 'Double',
        title: 'Overs'
    },
    primaryYAxis: {
        title: 'Runs'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'England', type: 'Area'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Customize Numeric Range**

Range of an axis, will be calculated automatically based on the provided data, you can also customize the
range of the axis using [`minimum`](../api/chart/axis/#minimum),
[`maximum`](../api/chart/axis/#maximum) and [`interval`](../api/chart/axis/#interval) property of
the axis.

{% tab template= "chart/axis", es5Template="es5DoubleRange" %}

```typescript

import { Chart, AreaSeries } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        // Numeric axis range
        minimum: 1,
        maximum: 20,
        interval: 5
        title: 'Overs'
    },
    primaryYAxis: {
        title: 'Runs',
        minimum: 0,
        maximum: 20,
        interval: 10
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'England', type: 'Area'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Apply Padding to the Range**

Padding can be applied to the minimum and maximum extremes of an axis range by using the
[`rangePadding`](../api/chart/axis/#rangepadding) property. Numeric axis supports the following types of
padding.

* None
* Round
* Additional
* Normal
* Auto

**Numeric - None**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `None`, minimum and maximum of the axis is based on the data.

{% tab template= "chart/axis", es5Template="es5DoubleNone" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        title: 'Overs'
    },
    primaryYAxis: {
        valueType: 'Double',
        title: 'Runs',
        //RangePadding as none in Y Axis
        rangePadding: 'None'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', width: 3,
        name: 'England', type: 'Line'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Numeric - Round**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Round`, minimum and maximum will
be rounded to the nearest possible value, which is divisible by interval. For example, when the minimum is 3.5 and
the interval is 1, then the minimum will be rounded to 3.

{% tab template= "chart/axis", es5Template="es5DoubleRound" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        title: 'Overs'
    },
    primaryYAxis: {
        valueType: 'Double',
        title: 'Runs',
        //RangePadding as round in Y Axis
        rangePadding: 'Round'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', width: 3,
        name: 'England', type: 'Line'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Numeric - Additional**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Additional`, interval of an axis
will be padded to the minimum and maximum of the axis.

{% tab template= "chart/axis", es5Template="es5DoubleAdditional" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        title: 'Overs'
    },
    primaryYAxis: {
        valueType: 'Double',
        title: 'Runs',
        //RangePadding as additional in Y Axis
        rangePadding: 'Additional'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', width: 3,
        name: 'England', type: 'Line'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Numeric - Normal**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Normal`, padding is applied to the axis based on default range calculation.

{% tab template= "chart/axis", es5Template= "es5DoubleNormal" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        title: 'Overs'
    },
    primaryYAxis: {
        valueType: 'Double',
        title: 'Runs',
        //RangePadding as normal in Y Axis
        rangePadding: 'Normal'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', width: 3,
        name: 'England', type: 'Line'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

**Numeric - Auto**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Auto`, horizontal numeric axis
takes None as padding calculation, while the vertical numeric axis takes Normal as padding calculation.

{% tab template= "chart/axis", es5Template="es5DoubleAuto" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 1, y: 7 }, { x: 2, y: 1 }, { x: 3, y: 1 },
    { x: 4, y: 14 }, { x: 5, y: 1 }, { x: 6, y: 10 },
    { x: 7, y: 8 }, { x: 8, y: 6 }, { x: 9, y: 10 },
    { x: 10, y: 10 }, { x: 11, y: 16 }, { x: 12, y: 6 },
    { x: 13, y: 14 }, { x: 14, y: 7 }, { x: 15, y: 5 },
    { x: 16, y: 2 }, { x: 17, y: 14 }, { x: 18, y: 7 },
    { x: 19, y: 7 }, { x: 20, y: 10 }];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Double',
        title: 'Overs',
        // Set the rangePadding as auto in Y Axis
        rangePadding: 'Auto'
    },
    primaryYAxis: {
        valueType: 'Double',
        title: 'Runs',
        // Set the rangePadding as auto in Y Axis
        rangePadding: 'Auto'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y', width: 3,
        name: 'England', type: 'Line'
    }],
    title: 'England - Run Rate'
}, '#element');

```

{% endtab %}

## DateTime Axis

Date time axis uses date time scale and displays the date time values as axis labels in the specified format.

{% tab template= "chart/axis", es5Template="es5DateTime" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        // Date time scale in primary X Axis
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Customizing Date Time Range**

Range of an axis will be calculated automatically based on the provided data, you can also customize the
range of the axis using [`minimum`](../api/chart/axis/#minimum),
[`maximum`](../api/chart/axis/#maximum) and [`interval`](../api/chart/axis/#interval) property
of the axis.

{% tab template= "chart/axis", es5Template="es5DateTimeRange" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        // Date time range in primary X Axis
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        minimum: new Date(2000, 6, 1),
        maximum: new Date(2010, 6, 1)
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Date Time Intervals**

Date time intervals can be customized by using the [`interval`](./../api/chart/axis/#interval)
and [`intervalType`](../api/chart/axis/#intervaltype) properties of the axis.
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
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        minimum: new Date(2000, 6, 1),
        maximum: new Date(2010, 6, 1),
        interval: 2,
        //interval type as years in primary x axis
        intervalType: 'Years'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Applying Padding to the Range**

Padding can be applied to the minimum and maximum extremes of the range by using the
[`rangePadding`](../api/chart/axis/#rangepadding) property. Date time axis supports the
following types of padding,

* None
* Round
* Additional

**Datetime - None**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `None`, minimum and maximum of an axis is based on the data.

{% tab template= "chart/axis", es5Template="es5DateTimeNone" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        //Range padding as none
        rangePadding: 'None'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Datetime - Round**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Round`, minimum and maximum will
be rounded to the nearest possible value, which is divisible by interval. For example, when the minimum is
15th Jan, interval is 1 and the interval type is ‘month’, then the axis minimum will be Jan 1st.

{% tab template= "chart/axis", es5Template="es5DateTimeRound" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        //Range padding as round
        rangePadding: 'Round'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Datetime - Additional**

When the [`rangePadding`](../api/chart/axis/#rangepadding) is set to `Additional`, interval of an axis
will be padded to the minimum and maximum of the axis.

{% tab template= "chart/axis", es5Template="es5DateTimeAdditional" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        //Range padding as additional
        rangePadding: 'Additional'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

>Note: To use datetime axis, we need to inject DateTime using `Chart.Inject(DateTime)` method and
set the [`valueType`](../api/chart/axis/#valuetype) of axis to DateTime.

<!-- markdownlint-disable MD033 -->

## Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic axis uses logarithmic scale and it is very useful in visualizing data, when it has numerical values in
both lower order of magnitude (eg: 10<sup>-6</sup>) and higher order of magnitude (eg: 10<sup>6</sup>).

{% tab template= "chart/axis", es5Template="es5LogAxis" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Logarithmic);
let chartData: any[] = [
    { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
    { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
    { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
    { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
    { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
    { x: new Date(2005, 0, 1), y: 11000 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Years',
        labelFormat: 'y'
    },
    primaryYAxis: {
        // Logarithmic scale in primary X Axis
        valueType: 'Logarithmic',
        title: 'Profit'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Line'
    }],
    title: 'Product X Growth [1995-2005]'
}, '#element');

```

{% endtab %}

**Customize Logarithmic Range**

Range of an axis, will be calculated automatically based on the provided data, you can also customize the range of an axis using [`minimum`](../api/chart/axis/#minimum),[`maximum`](../api/chart/axis/#maximum)
and [`interval`](./../api/chart/axis/#interval) property of the axis.

{% tab template= "chart/axis", es5Template="es5LogRange" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Logarithmic);
let chartData: any[] = [
    { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
    { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
    { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
    { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
    { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
    { x: new Date(2005, 0, 1), y: 11000 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Years',
        labelFormat: 'y'
    },
    primaryYAxis: {
        //Logarithmic scale range in primary X Axis
        valueType: 'Logarithmic',
        title: 'Profit',
        minimum: 100,
        maximum: 10000
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Line'
    }],
    title: 'Product X Growth [1995-2005]'
}, '#element');

```

{% endtab %}

**Logarithmic Base**

Logarithmic base can be customized by using the [`logBase`](../api/chart/axis/#logbase) property of the axis.
For example when the logBase is 5, the axis values follows 5<sup>-2</sup>, 5<sup>-1</sup>, 5<sup>0</sup>,
5<sup>1</sup>, 5<sup>2</sup> etc.

{% tab template= "chart/axis", es5Template="es5LogBase" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Logarithmic);
let chartData: any[] = [
    { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
    { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
    { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
    { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
    { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
    { x: new Date(2005, 0, 1), y: 11000 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Years',
        labelFormat: 'y'
    },
    primaryYAxis: {
        valueType: 'Logarithmic',
        title: 'Profit',
        // logBase for logarithmic scale
        logBase: 2
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Line'
    }],
    title: 'Product X Growth [1995-2005]'
}, '#element');

```

{% endtab %}

**Logarithmic Interval**

Logarithmic axis interval can be customized by using the [`interval`](./../api/chart/axis/#interval)
property of the axis. When the logarithmic base is 10 and logarithmic interval is 2, then the axis labels
are placed at an interval of 10<sup>2</sup>. The default value of the interval is 1.

{% tab template= "chart/axis", es5Template="es5LogInterval" %}

```typescript

import { Chart, DateTime, LineSeries, Logarithmic } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Logarithmic);
let chartData: any[] = [
    { x: new Date(1995, 0, 1), y: 80 }, { x: new Date(1996, 0, 1), y: 200 },
    { x: new Date(1997, 0, 1), y: 400 }, { x: new Date(1998, 0, 1), y: 600 },
    { x: new Date(1999, 0, 1), y: 700 }, { x: new Date(2000, 0, 1), y: 1400 },
    { x: new Date(2001, 0, 1), y: 2000 }, { x: new Date(2002, 0, 1), y: 4000 },
    { x: new Date(2003, 0, 1), y: 6000 }, { x: new Date(2004, 0, 1), y: 8000 },
    { x: new Date(2005, 0, 1), y: 11000 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Years',
        labelFormat: 'y'
    },
    primaryYAxis: {
        //Logarithmic interval in primary X Axis
        valueType: 'Logarithmic',
        title: 'Profit',
        interval: 2
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Line'
    }],
    title: 'Product X Growth [1995-2005]'
}, '#element');

```

{% endtab %}

>Note: To use log axis, we need to inject `Logarithmic` using method `Chart.Inject(Logarithmic)` and
set the [`valueType`](../api/chart/axis/#valuetype) of axis to `Logarithmic`.

## Inversed Axis

<!-- markdownlint-disable MD033 -->

When an axis is inversed, highest value of the axis comes closer to origin and vice versa. To place an axis in inversed manner set this property
 [`isInversed`](../api/chart/axis/#isinversed) to true.

{% tab template= "chart/axis", es5Template="es5InversedAxis" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, DataLabel);
/**
 * inversed axis sample
 */
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
            title: 'Years',
            opposedPosition: true,
            isInversed: true
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Exchange rate (INR per USD)',
            edgeLabelPlacement: 'Shift',
            labelIntersectAction: 'Rotate45',
            isInversed: true
        },
        series: [
            {
                type: 'Column',
                dataSource: [
                    { x: 2008, y: 15.1 }, { x: 2009, y: 16 }, { x: 2010, y: 21.4 },
                    { x: 2011, y: 18 }, { x: 2012, y: 16.2 }, { x: 2013, y: 11 },
                    { x: 2014, y: 7.6 }, { x: 2015, y: 1.5 }
                ],
                marker: { dataLabel: { visible: true }},
                xName: 'x',
                yName: 'y', name: 'Years',
            },
        ],
        title: 'Exchange rate',
    }, '#element');

```

{% endtab %}

## Label Format

**Numeric Label Format**

Numeric labels can be formatted by using the [`labelFormat`](../api/chart/axis/#labelformat) property.
Numeric labels supports all globalize format.

{% tab template= "chart/axis", es5Template="es5LabelFormat" %}

```typescript

import { Chart, AreaSeries } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries);
let chartData: any[] = [
    { x: 1900, y: 4, y1: 2.6, y2: 2.8 }, { x: 1920, y: 3.0, y1: 2.8, y2: 2.5 },
    { x: 1940, y: 3.8, y1: 2.6, y2: 2.8 }, { x: 1960, y: 3.4, y1: 3, y2: 3.2 },
    { x: 1980, y: 3.2, y1: 3.6, y2: 2.9 }, { x: 2000, y: 3.9, y1: 3, y2: 2 }
]
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Year',
        edgeLabelPlacement: 'Shift'
    },
    primaryYAxis: {
        title: 'Sales Amount in Millions',
        //Label format as currency
        labelFormat: 'c'
    },
    series:[{
        dataSource: chartData, opacity: 0.6,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Area'
    },{
        dataSource: chartData, opacity: 0.6,
        xName: 'x', yName: 'y1',
        name: 'Product Y', type: 'Area'
    },{
        dataSource: chartData, opacity: 0.6,
        xName: 'x', yName: 'y2',
        name: 'Product Z', type: 'Area'
    }],
    title: 'Average Sales Comparison'
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
<td>$1,000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1,000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

**DateTime Label Format**

You can format and parse the date to all globalize format using [`labelFormat`](../api/chart/axis/#labelformat) property in an axis.

{% tab template= "chart/axis", es5Template="es5DateTimeFormat" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        //Label format as yMd
        labelFormat: 'yMd'
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
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

**Custom Label Format**

Axis also supports custom label format using placeholder like {value}°C, in which the value represent the axis label e.g 20°C.

{% tab template= "chart/axis", es5Template="es5CustomFormat" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals',
        // Custom label format
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Common Axis Features

**Axis Title**

You can add a title to the axis using [`title`](../api/chart/axis/#title) property to provide quick
information to the user about the data plotted in the axis.

{% tab template= "chart/axis", es5Template="es5AxisTitle" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals',
        labelFormat: '${value}K',
        //Axis title text style
        titleStyle: {
            size: '16px', color: 'grey',
            fontFamily : 'Segoe UI', fontWeight : 'bold'
        }
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Label Customization**

The [`labelStyle`](../api/chart/axis/#labelstyle) property of an axis provides options to
customize the `color`, `font-family`, `font-size` and `font-weight` of the axis labels.

{% tab template= "chart/axis", es5Template="es5LabelCustomization" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        labelPlacement: 'OnTicks',
        edgeLabelPlacement: 'Shift',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals',
        labelFormat: '${value}K',
        // Customization of the label
        labelStyle: {
            size: '14px', color: 'blue',
            fontFamily : 'Segoe UI', fontWeight : 'bold'
        }
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Edge Label Placement**

Labels with long text at the edges of an axis may appear partially in the chart. To avoid this,
use [`edgeLabelPlacement`](../api/chart/axis/#edgelabelplacement) property in axis, which
moves the label inside the chart area for better appearance or hides it.

{% tab template= "chart/axis", es5Template="es5EdgeLabel" %}

```typescript

import { Chart, DateTime, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime);
let chartData: any[] = [
    { x: new Date(2000, 6, 11), y: 10 }, { x: new Date(2002, 3, 7), y: 30 },
    { x: new Date(2004, 3, 6), y: 15 }, { x: new Date(2006, 3, 30), y: 65 },
    { x: new Date(2008, 3, 8), y: 90 }, { x: new Date(2010, 3, 8), y: 85 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
        title: 'Sales Across Years',
        labelFormat: 'yMMM',
        //Edgelabelplacement for primary x axis
        edgeLabelPlacement: 'Shift',
        minimum: new Date(2000, 6, 1),
        maximum: new Date(2010, 6, 1)
    },
    primaryYAxis: {
        title: 'Sales Amount in millions(USD)'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Line'
    }],
    title: 'Average Sales Comparison'
}, '#element');

```

{% endtab %}

**Grid Lines Customization**

You can customize the `width`, `color` and `dashArray` of the minor and major grid lines, using [`majorGridLines`](../api/chart/axis/#majorgridlines)
and [`minorGridLines`](../api/chart/axis/#minorgridlines) properties in the axis.

{% tab template= "chart/axis", es5Template="es5GridLines" %}

```typescript

import { Chart, Category, ColumnSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
    { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
    { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
    { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
    { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        //Grid lines customization
        majorGridLines : {
            color : 'blue',
            width : 1
        },
        minorGridLines : {
            color : 'red',
            width : 0
        }
    },
    primaryYAxis: {
        title: 'Temperature (Fahrenheit)',
        //Grid lines customization
        majorGridLines : {
            color : 'blue',
            width : 1
        },
        minorGridLines : {
            color : 'red',
            width : 0
        }
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Column'
    }],
    title: 'Temperature flow over months'
}, '#element');

```

{% endtab %}

**Tick Lines Customization**

You can customize the  `width`, `color` and `size` of the minor and major tick lines, using
[`majorTickLines`](../api/chart/axis/#majorticklines) and
[`minorTickLines`](../api/chart/axis/#minorticklines) properties in the axis.

{% tab template= "chart/axis", es5Template="es5TickLines" %}

```typescript

import { Chart, Category, ColumnSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
    { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
    { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
    { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
    { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        //Tick lines customization
        majorTickLines : {
            color : 'blue',
            width : 5
        },
        minorTickLines : {
            color : 'red',
            width : 0
        }
    },
    primaryYAxis: {
        title: 'Temperature (Fahrenheit)',
        //Grid lines customization
        majorTickLines : {
            color : 'blue',
            width : 5
        },
        minorTickLines : {
            color : 'red',
            width : 0
        }
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Column'
    }],
    title: 'Temperature flow over months'
}, '#element');

```

{% endtab %}

**Place Axes at the Opposite Side**

To place an axis opposite from its original position,
set [`opposedPosition`](../api/chart/axis/#opposedposition) property of the axis to true.

{% tab template= "chart/axis", es5Template="es5Opposed" %}

```typescript

import { Chart, Category, ColumnSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
    { x: 'Jan', y: 60 }, { x: 'Feb', y: 50 }, { x: 'Mar', y: 64 },
    { x: 'Apr', y: 63 }, { x: 'May', y: 81 }, { x: 'Jun', y: 64 },
    { x: 'Jul', y: 82 }, { x: 'Aug', y: 96 }, { x: 'Sep', y: 78 },
    { x: 'Oct', y: 60 }, { x: 'Nov', y: 58 }, { x: 'Dec', y: 56 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    primaryYAxis: {
        title: 'Temperature (Fahrenheit)',
        //Axis position as opposite
        opposedPosition: true
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Sales', type: 'Column'
    }],
    title: 'Temperature flow over months'
}, '#element');

```

{% endtab %}

## Multiple Axis

In addition to primary X and Y axis, we can add n number of axis to the chart. Series can be associated with
this axis, by mapping with axis's unique name.

{% tab template= "chart/axis", es5Template="es5MultipleAxis" %}

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
        labelFormat: '{value}°F'
    },
     // Initializing multiple axis
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 0, opposedPosition: true,
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
        xName: 'x', yName: 'y1', yAxisName: 'yAxis',
        name: 'Japan', type: 'Line',
        marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#F8AB1D' } }
    }],
    title: 'Weather Condition'
}, '#element');

```

{% endtab %}

## Smart Axis Labels

When the axis labels overlap with each other, you can use
[`labelIntersectAction`](../api/chart/axis/#labelintersectaction) property in the axis,
to place them smartly.

When setting `labelIntersectAction` as `Hide`

{% tab template= "chart/axis", es5Template="es5SmartAxis" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: "South Korea", y: 39.4 }, { x: "India", y: 61.3 }, { x: "Pakistan", y: 20.4 },
    { x: "Germany", y: 65.1 }, { x: "Australia", y: 15.8 }, { x: "Italy", y: 29.2 },
    { x: "United Kingdom", y: 44.6 }, { x: "Saudi Arabia", y: 9.7 }, { x: "Russia", y: 40.8 },
    { x: "Mexico", y: 31 }, { x: "Brazil", y: 75.9 }, { x: "China", y: 51.4 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Countries',
        valueType: 'Category',
        //label intersect as hide
        labelIntersectAction: 'Hide'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80, interval: 10,
        title: 'People(in millions)'
    },
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 0, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 2,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Internet', type: 'Column'
    }],
    title: 'Internet Users'
}, '#element');

```

{% endtab %}

When setting `labelIntersectAction` as `Rotate45`

{% tab template= "chart/axis", es5Template="es5labelIntersect" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: "South Korea", y: 39.4 }, { x: "India", y: 61.3 }, { x: "Pakistan", y: 20.4 },
    { x: "Germany", y: 65.1 }, { x: "Australia", y: 15.8 }, { x: "Italy", y: 29.2 },
    { x: "United Kingdom", y: 44.6 }, { x: "Saudi Arabia", y: 9.7 }, { x: "Russia", y: 40.8 },
    { x: "Mexico", y: 31 }, { x: "Brazil", y: 75.9 }, { x: "China", y: 51.4 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Countries',
        valueType: 'Category',
        // label intersect as 45
        labelIntersectAction: 'Rotate45'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80, interval: 10,
        title: 'People(in millions)'
    },
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 0, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 2,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Internet', type: 'Column'
    }],
    title: 'Internet Users'
}, '#element');

```

{% endtab %}

When setting `labelIntersectAction` as `Rotate90`

{% tab template= "chart/axis", es5Template="es5LabelIntersect45" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
let chartData: any[] = [
    { x: "South Korea", y: 39.4 }, { x: "India", y: 61.3 }, { x: "Pakistan", y: 20.4 },
    { x: "Germany", y: 65.1 }, { x: "Australia", y: 15.8 }, { x: "Italy", y: 29.2 },
    { x: "United Kingdom", y: 44.6 }, { x: "Saudi Arabia", y: 9.7 }, { x: "Russia", y: 40.8 },
    { x: "Mexico", y: 31 }, { x: "Brazil", y: 75.9 }, { x: "China", y: 51.4 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Countries',
        valueType: 'Category',
        // label intersect as 90
        labelIntersectAction: 'Rotate90'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80, interval: 10,
        title: 'People(in millions)'
    },
    axes:[
        {
            majorGridLines: { width: 0 },
            rowIndex: 0, opposedPosition: true,
            lineStyle: { width: 0 },
            minimum: 24, maximum: 36, interval: 2,
            name: 'yAxis', title: 'Temperature (Celsius)',
            labelFormat: '{value}°C'
        }
    ],
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Internet', type: 'Column'
    }],
    title: 'Internet Users'
}, '#element');

```

{% endtab %}

## Strip lines

EJ2 chart supports horizontal and vertical strip lines and customization of stripline in both orientation.
To use strip line in axis, we need to inject `StripLine` module using `Chart.Inject(StripLine)` method

### Horizontal Strip lines

You can create Horizontal stripline by adding the <code>stripline</code> in the vertical axis and set <code>visible</code> option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis", es5Template="es5StripLinesHorizontal" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries, DataLabel, StripLine);
let chartData: any[] = [
   {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
   {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 20},{x: 10, y: 7},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Overs'
    },
    primaryYAxis: {
        title: 'Runs',
        stripLines:[
            { start: 15, end: 22, text: 'Good', color: '#ff512f', visible: true, zIndex: 'Behind', opacity: 0.5 }
            { start: 8, end: 15, text: 'Medium', color: 'pink', opacity: 0.5, visible: true, zIndex: 'Behind' }
            { start: 0, end: 8, text:'Not enough', color: 'skyblue', opacity: 0.5, visible: true, zIndex: 'Behind' }]
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Column',
        marker: { dataLabel: { visible: true}}
    }],
    title: 'India Vs Australia 1st match',
}, '#element');

```

{% endtab %}

### Vertical Striplines

You can create vertical stripline by adding the <code>stripline</code> in the horizontal axis and set <code>visible</code> option to true.
Striplines are rendered in the specified start to end range and you can add more than one stripline for an axis.

{% tab template= "chart/axis", es5Template="es5StripLinesVertical" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries, DataLabel, StripLine);
let chartData: any[] = [
   {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
   {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 34},{x: 10, y: 7},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Overs',
        stripLines:[
            {start: 0, end: 5, text: 'powerplay 1', color: 'red', visible: true, opacity: 0.5, rotation: 45, testStyle: { size: 20, color: 'black'}},
            {start: 5, end: 10, text: 'powerplay 2', color: 'blue', visible: true, opacity: 0.5, rotation: 45, testStyle: { size: 20, color: 'black'}},
        ]
    },
    primaryYAxis: {
        title: 'Runs'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Column',
        marker: { dataLabel: { visible: true}}
    }],
    title: 'India Vs Australia 1st match',
}, '#element');

```

{% endtab %}

### Customize the strip line

Starting value in specific strip line can be customized by <code>start</code> property in strip line. Similarly, ending value is customized by <code>end</code>. It can be also set for starting from the corresponding origin of the axis by
<code>startFromOrigin</code>. Size of the strip line is customized by <code>size</code>. Border for the stripline is customized by <code>border</code>. Order of the strip line such that whether it should be rendered in behind or over the series elements
is customized by <code>zIndex</code>.

{% tab template= "chart/axis", es5Template="es5StripLineCus" %}

```typescript

import { Chart, ColumnSeries, LineSeries, DataLabel, StripLine } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, LineSeries, DataLabel, StripLine);
let chartData: any[] = [
   {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
   {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 34},{x: 10, y: 7},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Overs',
        stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5}
        ]
    },
    primaryYAxis: {
        title: 'Runs'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Column',
        marker: { dataLabel: { visible: true }}
    }],
    title: 'India Vs Australia 1st match',
}, '#element');

```

{% endtab %}

### Customize the stripline text

You can customize the text rendered in stripline by <code>textStyle</code> property. Rotation of the strip line text can be changed by <code>rotation</code> property.
Horizontal and Vertical alignment of stripline text can be changed by <code>horizontalAlignment</code> and <code>verticalAlignment</code> property.

{% tab template= "chart/axis", es5Template="es5StripLineText" %}

```typescript

import { Chart, ColumnSeries, LineSeries, StripLine } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, LineSeries, StripLine);
let chartData: any[] = [
   {x: 1, y: 20},{x: 2, y: 22},{x: 3, y: 0},{x: 4, y: 12},{x: 5, y: 5},
   {x: 6, y: 15},{x: 7, y: 6},{x: 8, y: 12},{x: 9, y: 34},{x: 10, y: 7},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Overs',
        stripLines:[
            { startFromOrigin: true, size: 4, zIndex: 'Behind', opacity: 0.5,  text: 'Good', verticalAlignment: 'Middle', horizontalAlignment: 'Middle', rotation: 90, textStyle: { size: 15}},
            { start: 5, end: 8, verticalAlignment: 'Start', horizontalAlignment: 'End', rotation: 45, text: 'Poor'}
        ]
    },
    primaryYAxis: {
        title: 'Runs'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        type: 'Column',
        marker: { visible: true}
    }],
    title: 'India Vs Australia 1st match',
}, '#element');

```

{% endtab %}