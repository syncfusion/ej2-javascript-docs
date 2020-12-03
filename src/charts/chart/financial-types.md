---
title: " Financial charts | TypeScript "

component: "Chart"

description: "Financial charts are used to illustrate the movements in the price of a financial instrument over time. chart have hilo, hiloopenclose,candle."
---

# Financial Charts

Financial charts are used to illustrate the movements in the price of a financial instrument over time.

Chart supports the following financial series

<!-- markdownlint-disable MD036 -->

**Hilo**

Hilo Series illustrates the price movements in stock using the high and low values.
To render a Hilo series, use series [`type`](../api/chart/seriesModel/#type-string)
as `Hilo` and inject `HiloSeries` module using `Chart.Inject(HiloSeries)` method.

Hilo series requires 3 fields (x, high and low) to show the high and low price in the stock.

{% tab template= "chart/chart-types", es5Template="es5Hilo"%}

```typescript

import { Chart, HiloSeries,Category } from '@syncfusion/ej2-charts';
Chart.Inject(HiloSeries, Category);
let chartData: any[] = [
    { x: 'Jan', low: 87, high: 200 }, { x: 'Feb', low: 45, high: 135 },
    { x: 'Mar', low: 19, high: 85 }, { x: 'Apr', low: 31, high: 108 },
    { x: 'May', low: 27, high: 80 }, { x: 'June', low: 84, high: 130 },
    { x: 'July', low: 77, high: 150 }, { x: 'Aug', low: 54, high: 125 },
    { x: 'Sep', low: 60, high: 155 }, { x: 'Oct', low: 60, high: 180 },
    { x: 'Nov', low: 88, high: 180 }, { x: 'Dec', low: 84, high: 230 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[
        {
            dataSource: chartData,
            xName: 'x', high: 'high', low: 'low',
            //Series type as Hilo
            type: 'Hilo'
        }
    ],
}, '#element');

```

{% endtab %}

**High Low Open Close**

HiloOpenClose series is used to represent the low, high, open and closing values over time.
To render a HiloOpenClose series, use series [`type`](../api/chart/seriesModel/#type-string)
as `HiloOpenClose` and inject `HiloOpenCloseSeries` module using `Chart.Inject(HiloOpenCloseSeries)` method.

HiloOpenClose series requires 5 fields (x, high, low, open and close) to show the high, low, open and close price values in the stock.

{% tab template= "chart/chart-types", es5Template="es5HiloOpenClose" %}

```typescript

import { Chart, HiloOpenCloseSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(HiloOpenCloseSeries, Category);
let chartData: any[] = [
    { x: 'Jan', open: 120, high: 160, low: 100, close: 140 },
    { x: 'Feb', open: 150, high: 190, low: 130, close: 170 },
    { x: 'Mar', open: 130, high: 170, low: 110, close: 150 },
    { x: 'Apr', open: 160, high: 180, low: 120, close: 140 },
    { x: 'May', open: 150, high: 170, low: 110, close: 130 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[
        {
            dataSource: chartData,
            xName: 'x', open: 'open', close: 'close', high: 'high', low: 'low',
            // Series type as HiloOpenClose
            type: 'HiloOpenClose'
        }
    ],
    title: 'Financial Analysis'
}, '#element');

```

{% endtab %}

**Customization of HiloOpenClose Series**

In HiloOpenClose series, [`bullFillColor`](../api/chart/seriesModel/#fill-string) is used to fill the segment when
the open value is greater than the close value and [`bearFillColor`](../api/chart/seriesModel/#fill-string) is
used to fill the segment when the open value is less than the close value.

By default, bullFillColor is set as red and bearFillColor is set as green.

{% tab template= "chart/chart-types", es5Template="es5HiloOpenCloseCust" %}

```typescript

import { Chart, HiloOpenCloseSeries, Category } from '@syncfusion/ej2-charts';
import { hocData } from './datasource.ts';
Chart.Inject(HiloOpenCloseSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series: [
        {
            type: 'HiloOpenClose',
            // sets the bullFill and bearFill color of hiloopenclose chart
            bearFillColor: '#e56590',
            bullFillColor: '#f8b883',
            dataSource: hocData,
            xName: 'x', open: 'open', close: 'close', high: 'high', low: 'low',
        }
    ],
}, '#element');

```

{% endtab %}

**Candle**

Candle series is similar to Hilo Open Close series, are used to represent the low,
high, open and closing price over time. To render a candle series, use series [`type`](../api/chart/seriesModel/#type-string)
as `Candle` and inject `CandleSeries` module using `Chart.Inject(CandleSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Candle" %}

```typescript

import { Chart, CandleSeries, Category, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(CandleSeries, Category, DateTime);
let chartData: any[] = [
    { x: 'Jan', open: 120, high: 160, low: 100, close: 140 },
    { x: 'Feb', open: 150, high: 190, low: 130, close: 170 },
    { x: 'Mar', open: 130, high: 170, low: 110, close: 150 },
    { x: 'Apr', open: 160, high: 180, low: 120, close: 140 },
    { x: 'May', open: 150, high: 170, low: 110, close: 130 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[
        {
            dataSource: chartData,
            xName: 'x', open: 'open', close: 'close', high: 'high', low: 'low',
            // Series type as candle series
            type: 'Candle'
        }
    ],
}, '#element');

```

{% endtab %}

**Hollow Candles**

Candle charts allow to visually compare the current price with previous price by coloring them.

Candles are filled/left as hollow based on the following criteria.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>States</b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>Filled</td>
<td>candle sticks are filled when the close value is lesser than the open value</td>
</tr>
<tr>
<td>Unfilled</td>
<td>candle sticks are unfilled when the close value is greater than the open value</td>
</tr>
</table>

The color of the candle will be defined by comparing with previous values.
Bear color will be applied when the current closing value is greater than the previous closing value.
Bull color will be applied when the current closing value is less than the previous closing value.

By default, bullFillColor is set as red and bearFillColor is set as green.

**Solid Candles**

[`enableSolidCandles`](../api/chart/seriesModel/#enableSolidCandles-string) is used to enable/disable the solid candles.
By default is set to be false.
The fill color of the candle will be defined by its opening and closing values.

[`bearFillColor`](../api/chart/seriesModel/#bearFillColor-string) will be applied when the opening value is less than the closing value.
[`bullFillColor`](../api/chart/seriesModel/#bullFillColor-string) will be applied when the opening value is greater than closing value.

{% tab template= "chart/chart-types", es5Template="es5Candle-solid" %}

```typescript

import { Chart, CandleSeries, Category, DateTime } from '@syncfusion/ej2-charts';
import { hocData } from './datasource.ts';
Chart.Inject(CandleSeries, Category, DateTime);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[
        {
            dataSource: hocData,
            xName: 'x', open: 'open', close: 'close', high: 'high', low: 'low',
            bearFillColor: '#e56590',
            bullFillColor: '#f8b883',
            // Series type as candle series
            type: 'Candle'
        }
    ],
    title: 'Shirpur Gold Refinery Share Price'
}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)