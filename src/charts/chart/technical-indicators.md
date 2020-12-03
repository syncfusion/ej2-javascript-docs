---
title: " Chart Technical Indicators | TypeScript "

component: "Chart"

description: "Indicators represent a statistical approach to technical analysis as opposed to a subjective approach. we have different types of indicators."
---
<!-- markdownlint-disable MD036 -->

# Technical Indicators

A technical indicator is a mathematical calculation based on historic price, volume or open interest information
that aims to forecast financial market direction.

Chart supports 10 types of technical indicators.

## Accumulation Distribution

Accumulation Distribution combines price and volume to show how money may be flowing into or out of stock.
To render a Accumulation Distribution Indicator,
use indicator [`type`](../api/chart/technicalIndicatorModel/) as `AccumulationDistribution` and inject
`AccumulationDistributionIndicator` module using `Chart.Inject(AccumulationDistributionIndicator)`.
To calculate the signal line [`volume`](../api/chart/technicalIndicatorModel/) field is additionally added with `dataSource`.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5AdIndicator" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, AccumulationDistributionIndicator, Tooltip, Crosshair, IAxisLabelRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, AccumulationDistributionIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30,
        maximum: 180,
        interval: 30,
    },
    axes: [{
        name: 'secondary',
        minimum: -7000000000, maximum: 5000000000,
        interval: 6000000000,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', volume: 'volume', open: 'open',
        name: 'Apple Inc',
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'AccumulationDistribution', field: 'Close', seriesName: 'Apple Inc', yAxisName: 'secondary', fill: 'blue',
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    axisLabelRender: (args: IAxisLabelRenderEventArgs) => {
            if (args.axis.name === 'secondary') {
                let value: number = Number(args.text) / 1000000000;
                args.text = String(value) + 'bn';
            }
        },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Average True Range (ATR)

ATR measures the stock volatility by comparing the current value with the previous value.
To render a Average True Range (ATR) Indicator,
use indicator [`type`](../api/chart/technicalIndicatorModel/) as `Atr` and inject `AtrIndicator` module using `Chart.Inject(AtrIndicator)`.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5ATR" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, AtrIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, AtrIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0},
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30,
        maximum: 180,
        interval: 30,
    },
    axes: [{
       name: 'secondary',
       minimum:0,maximum:15,
       majorGridLines: { width: 0 },
       opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close : 'close', volume: 'volume',open:'open',
        name: 'Apple Inc',
         //Series type as RangeColumn
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'Atr', field: 'Low', seriesName: 'Apple Inc', yAxisName: 'secondary', fill: 'blue',
        period: 3, animation: { enable: true}
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Bollinger Band

A chart overlay that shows the upper and lower limits of normal price movements based on the standard deviation of prices.
To render a Bollinger Band, use indicator [`type`](../api/chart/technicalIndicatorModel/) as `BollingerBand`
and inject `BollingerBands` module using `Chart.Inject(BollingerBands)` method.
Bollinger band will be represented by three lines (upperLine, lowerLine, signalLine).
The default values of the Bollinger Band [`period`](../api/chart/technicalIndicatorModel/) is 14 and [`standardDeviations`](../api/chart/technicalIndicatorModel/) is 2.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5BollingerBand" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, BollingerBands, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, BollingerBands, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0},
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30,
        maximum: 180,
        interval: 30
    },
    series:[{
        dataSource: chartData, width: 2, low: 'low', high: 'high', close: 'close', open: 'open',
        xName: 'x', yName: 'y',
        name: 'USA',
        type: 'Candle',
    }],
    indicators: [{
        type: 'BollingerBands', field: 'Close', seriesName: 'USA', fill: 'blue',
        period: 3, animation: { enable: true }, upperLine: { color: 'orange' }, lowerLine: { color: 'yellow' }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Customization of BollingerBand**

`stroke`, `stroke-width`, and `color` of upperLine can be customized by using,[`upperLine`](../api/chart/technicalIndicatorModel/),
and the lowerLine can be customized by using [`lowerLine`](../api/chart/technicalIndicatorModel/) properties of indicator.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5BollingerCust" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, BollingerBands, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, BollingerBands, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30,
        maximum: 180,
        interval: 30
    },
    series:[{
        dataSource: chartData, width: 2, low: 'low', high: 'high', close: 'close', open: 'open',
        xName: 'x', yName: 'y',
        name: 'USA',
        type: 'Candle',
    }],
    indicators: [{
         type: 'BollingerBands',
         field: 'Close', seriesName: 'USA',
         fill: 'blue',
         period: 3,upperLine: { color: 'red' },
         lowerLine: { color: 'green' }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Exponential Moving Average (EMA)

Moving average Indicators are used to define the direction of the trend. To render a EMA Indicator,
use indicator [`type`](../api/chart/technicalIndicatorModel/) as `Ema` and
inject `EmaIndicator` module using `Chart.Inject(EmaIndicator)`.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5EMA" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, EmaIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, EmaIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
 primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30, maximum: 180, interval: 30,
        majorGridLines: { width: 0 }
    },
    axes: [{
        name: 'secondary',
        minimum: 30,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', volume: 'volume', open: 'open',
        name: 'Apple Inc',
        //Series type as RangeColumn
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'Ema', field: 'Close', seriesName: 'Apple Inc', fill: 'blue',
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Momentum

Momentum shows the speed at which the price of the stock is changing. To render a Momentum indicator, use indicator
[`type`](../api/chart/technicalIndicatorModel/) as `Momentum`and inject `MomentumIndicator` module using
`Chart.Inject(MomentumIndicator)` method. Momentum indicator will be represented by two lines (upperLine,
signalLine).In momentum indicator the upperBand value is always renders at the value 100.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5Momentum" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, MomentumIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, MomentumIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30, maximum: 180, interval: 30,
        majorGridLines: { width: 0 }
    },
    axes: [{
        name: 'secondary',
        minimum: 30,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', open: 'open',
        name: 'USA', animation: { enable: true },
        // Series type as StepLine
        type: 'Candle',
    }],
    indicators: [{
        type: 'Momentum', field: 'Close', seriesName: 'USA', yAxisName: 'secondary',
        upperLine: { color: 'red' },
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Customization of MomentumIndicator**

`stroke`, `stroke-width`, and `color` of upperLine can be customized by using [`upperLine`](../api/chart/technicalIndicatorModel/)
property of indicator.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5MomentumCust" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, MomentumIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, MomentumIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
       title: 'Price (Million Dollars)',
       minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
       name: 'secondary',
       minimum: 30,
       maximum: 110,
       majorGridLines: { width: 0 },
       opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', open: 'open',
        name: 'USA', animation: { enable: true },
        // Series type as StepLine
        type: 'Candle',
    }],
    indicators: [{
        type: 'Momentum', field: 'Close', seriesName: 'USA', yAxisName: 'secondary',
        upperLine: { color: 'red' },
        period: 3, animation: { enable: true },
        upperLine: { color: 'green' }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Moving Average Convergence Divergence (MACD)

MACD is based on the difference between two EMA's. To render a MACD Indicator, use indicator [`type`](../api/chart/technicalIndicatorModel/) as
`Macd` and inject `MacdIndicator` module using `Chart.Inject(MacdIndicator)`.MACD indicator will be represented
by MACD line,signal line, MACD histogram. MACD histogram is used to differentiate MACD line and signal line.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5MACD" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, MacdIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, MacdIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30, maximum: 180, interval: 30,
    },
    axes: [{
       name: 'secondary',
       majorGridLines: { width: 0 },
       opposedPosition: true
    }],
    series:[{
        name: 'gold',
        type: 'Candle',
        xName: 'x',
        low: 'low',
        high: 'high',
        open: 'open',
        animation: { enable: true },
        close: 'close',
        dataSource: chartData
    }],
    indicators: [{
        type: 'Macd',
        period: 3,
        fastPeriod: 5,
        slowPeriod: 2,
        seriesName: 'gold',
        macdType: 'Both',
        width: 2,
        fill: 'blue',
        yAxisName: 'secondary',
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Customization of MACD**

`stroke`, `stroke-width`, and `color`of macdLine can be customized by using,[`macdLine`](../api/chart/technicalIndicatorModel/),
property of indicator. The positive and negative changes of histogram can be customized by [`macdPositiveColor`](../api/chart/technicalIndicatorModel/)
and [`macdNegativeColor`](../api/chart/technicalIndicatorModel/) properties. The [`macdType`] is used to define the type of
MACD indicator. To customize the MACD period using [`slowPeriod`](../api/chart/technicalIndicatorModel/) and [`fastPeriod`](../api/chart/technicalIndicatorModel/)
properties.

By default `macdType` as 'Both'.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5MACDCust" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, MacdIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, MacdIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
       title: 'Price (Million Dollars)',
       minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
       name: 'secondary',
       majorGridLines: { width: 0 },
       opposedPosition: true
    }],
    series:[{
        name: 'gold',
        type: 'Candle',
        xName: 'x',
        low: 'low',
        high: 'high',
        open: 'open',
        animation: { enable: true },
        close: 'close',
        dataSource: chartData
    }],
    indicators: [{
        type: 'Macd',
        period: 3,
        fastPeriod: 5,
        slowPeriod: 2,
        seriesName: 'gold',
        macdType: 'Both',
        width: 2,
        fill: 'blue',
        yAxisName: 'secondary',
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Relative Strength Index (RSI)

RSI shows how strongly a stock is moving in its current direction. To render a RSI Indicator, use indicator [`type`](../api/chart/technicalIndicatorModel/) as
`Rsi` and inject `RsiIndicator` module using `Chart.Inject(Rsindicator)`.RSI indicator will be represented
by three lines (upperBand, lowerBand, signalLine). The upperBand and lowerBand values are customized by
[`overBought`](../api/chart/technicalIndicatorModel/) and [`overSold`](../api/chart/technicalIndicatorModel/)
properties of indicator and the signalLine is calculated by RSI formula.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5RSI" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, RsiIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, RsiIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
        name: 'secondary',
        minimum: 10,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2, low: 'low', high: 'high', close: 'close', open: 'open',
        xName: 'x', yName: 'y',
        name: 'USA',
        type: 'Candle',
    }],
    indicators: [{
        type: 'Rsi', field: 'Close', seriesName: 'USA', yAxisName: 'secondary', fill: 'blue',
        showZones: true, overBought: 70, overSold: 30,
        period: 3, animation: { enable: true }, upperLine: { color: 'red' }, lowerLine: { color: 'green' }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Simple Moving Average (SMA)

Moving average Indicators are used to define the direction of the trend. To render a SMA Indicator, use indicator [`type`](../api/chart/technicalIndicatorModel/) as
`Sma` and inject `SmaIndicator` module using `Chart.Inject(SmaIndicator)`.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5SMA" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, SmaIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, SmaIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
       title: 'Price (Million Dollars)',
       minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
        name: 'secondary',
        minimum: 30,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', volume: 'volume', open: 'open',
        name: 'Apple Inc',
        //Series type as RangeColumn
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'Sma', field: 'Close', seriesName: 'Apple Inc', fill: 'blue',
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Stochastic

It shows how a stock is, when compared to previous state. To render a Stochastic indicator, use indicator [`type`](../api/chart/technicalIndicatorModel/) as `Stochastic`
and inject `StochasticIndicator` module using `Chart.Inject(StochasticIndicator)` method.
stochastic indicator will be represented by four lines (upperLine, lowerLine, periodLine, signalLine).
In stochastic indicator the upperBand value and lowerBand value is customized by [`overBought`](../api/chart/technicalIndicatorModel/) and [`overSold`](../api/chart/technicalIndicatorModel/)
properties of indicators and the periodLine and signalLine is render based on stochastic formula.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5Stochastic" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, StochasticIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, StochasticIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
       title: 'Price (Million Dollars)',
       minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
        name: 'secondary',
        minimum: 10,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2, low: 'low', high: 'high', close: 'close', open: 'open',
        xName: 'x', yName: 'y',
        name: 'USA',
        type: 'Candle',
    }],
    indicators: [{
        type: 'Stochastic', field: 'Close', seriesName: 'USA', yAxisName: 'secondary', fill: 'blue',
        kPeriod: 2, dPeriod: 3, showZones: true,
        period: 3, animation: { enable: false },
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Customization of StochasticIndicator**

`stroke`, `stroke-width`, and `color` of upperLine can be customized by using,[`upperLine`](../api/chart/technicalIndicatorModel/),
the lowerLine can be customized by using [`lowerLine`](../api/chart/technicalIndicatorModel/) and the periodLine can be customized
by using [`periodLine`](../api/chart/technicalIndicatorModel/) properties of indicator. To customize the period to find the
average price using [`kPeriod`](../api/chart/technicalIndicatorModel/) and [`dPeriod`](../api/chart/technicalIndicatorModel/)
properties.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5StochasticCust" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, StochasticIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, StochasticIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143, close: 75.2857, volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
      title: 'Price (Million Dollars)',
      minimum: 30, maximum: 180, interval: 30
    },
    axes:[{
        name: 'secondary',
        minimum: 10,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2, low: 'low', high: 'high', close: 'close', open: 'open',
        xName: 'x', yName: 'y',
        name: 'USA',
        type: 'Candle',
    }],
    indicators: [{
        type: 'Stochastic', field: 'Close', seriesName: 'USA', yAxisName: 'secondary', fill: 'blue',
        kPeriod: 2, dPeriod: 3, showZones: true, periodLine: { color: 'yellow' },
        period: 3, animation: { enable: false }, upperLine: { color: 'red' }, lowerLine: { color: 'green' }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

## Triangular Moving Average (TMA)

Moving average Indicators are used to define the direction of the trend. To render a TMA Indicator, use indicator [`type`](../api/chart/technicalIndicatorModel/) as
`Tma` and inject `TmaIndicator` module using `Chart.Inject(TmaIndicator)`.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5TMA" %}

```typescript

import { Chart, LineSeries, CandleSeries,DateTime, TmaIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, CandleSeries,DateTime, TmaIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
         title: 'Months',
         valueType: 'DateTime',
         intervalType: 'Months',
         majorGridLines: { width: 0 },
         crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
         title: 'Price (Million Dollars)',
         minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
        name: 'secondary',
        minimum: 30,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', volume: 'volume', open: 'open',
        name: 'Apple Inc',
        //Series type as RangeColumn
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'Tma', field: 'Close', seriesName: 'Apple Inc', fill: 'blue',
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Customization of Technical Indicators**

`stroke`, `stroke-width`, and `color` of signalLine can be customized by using,[`fill`](../api/chart/technicalIndicatorModel/),
[`width`](../api/chart/technicalIndicatorModel/) and [`dashArray`](../api/chart/technicalIndicatorModel/) properties.
and the [`period`](../api/chart/technicalIndicatorModel/) property is used to predict the data forecast
calculations. The [`field`](../api/chart/technicalIndicatorModel/) value is used to the compare the current price
with previous price. It is applicable to Bollinger bands and moving averages. The [`showZones`](../api/chart/technicalIndicatorModel/#showzones)
property is used to shows/Hides the overBought and overSold regions. It is applicable for RSI and stochastic indicators.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5TMACust" %}

```typescript

import { Chart, LineSeries, CandleSeries,DateTime, TmaIndicator, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, CandleSeries,DateTime, TmaIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30, maximum: 180, interval: 30
    },
    axes: [{
        name: 'secondary',
        minimum: 30,
        maximum: 110,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    series:[{
        dataSource: chartData, width: 2,
        xName: 'x', yName: 'y', low: 'low', high: 'high', close: 'close', volume: 'volume', open: 'open',
        name: 'Apple Inc',
        //Series type as RangeColumn
        type: 'Candle', animation: { enable: true }
    }],
    indicators: [{
        type: 'Tma', field: 'Low', seriesName: 'Apple Inc', fill: 'red',
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}

**Data Source**

Usually technical indicators are added along with a financial series. The [`seriesName`](../api/chart/technicalIndicatorModel/)
represents the series, the data of which has to be analysed through indicators.

Technical indicators can also be added without series using [`dataSource`](../api/chart/technicalIndicatorModel/) property of indicator.

{% tab template= "chart/technical-indicators", isDefaultActive=true, es5Template="es5IndicatorData" %}

```typescript

import { Chart, LineSeries, DateTime, CandleSeries, AccumulationDistributionIndicator, Tooltip, Crosshair, IAxisLabelRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, CandleSeries, AccumulationDistributionIndicator, Tooltip, Crosshair);
let chartData: any[] = [
    {x: new Date('2012-10-15'), open: 90.3357, high: 93.2557, low: 87.0885,close: 87.12,volume: 646996264},
    {x: new Date('2012-10-22'), open: 87.4885, high: 90.7685, low: 84.4285,close: 86.2857,volume: 866040680 },
    {x: new Date('2012-10-29'), open: 84.9828, high: 86.1428, low: 82.1071,close: 82.4,volume: 367371310},
    {x: new Date('2012-11-05'), open: 83.3593, high: 84.3914, low: 76.2457,close: 78.1514,volume: 919719846},
    {x: new Date('2012-11-12'), open: 79.1643, high: 79.2143, low: 72.25,close: 75.3825,volume: 894382149},
    {x: new Date('2012-11-19'), open: 77.2443, high: 81.7143, low: 77.1257,close: 81.6428,volume: 527416747},
    {x: new Date('2012-11-26'), open: 82.2714, high: 84.8928, low: 81.7514,close: 83.6114,volume: 646467974},
    {x: new Date('2012-12-03'), open: 84.8071, high: 84.9414, low: 74.09,close: 76.1785,volume: 980096264},
    {x: new Date('2012-12-10'), open: 75, high: 78.5085, low: 72.2257,close: 72.8277,volume: 835016110},
    {x: new Date('2012-12-17'), open: 72.7043, high: 76.4143, low: 71.6043,close: 74.19,volume: 726150329},
    {x: new Date('2012-12-24'), open: 74.3357, high: 74.8928, low: 72.0943,close: 72.7984,volume: 321104733},
    {x: new Date('2012-12-31'), open: 72.9328, high: 79.2857, low: 72.7143,close: 75.2857,volume: 540854882},
    {x: new Date('2013-01-07'), open: 74.5714, high: 75.9843, low: 73.6,close: 74.3285,volume: 574594262},
    {x: new Date('2013-01-14'), open: 71.8114, high: 72.9643, low: 69.0543,close: 71.4285,volume: 803105621},
    {x: new Date('2013-01-21'), open: 72.08, high: 73.57, low: 62.1428,close: 62.84,volume: 971912560},
    {x: new Date('2013-01-28'), open: 62.5464, high: 66.0857, low: 62.2657,close: 64.8028,volume: 656549587},
    {x: new Date('2013-02-04'), open: 64.8443, high: 68.4014, low: 63.1428,close: 67.8543,volume: 743778993},
    {x: new Date('2013-02-11'), open: 68.0714, high: 69.2771, low: 65.7028,close: 65.7371,volume: 585292366},
    {x: new Date('2013-02-18'), open: 65.8714, high: 66.1043, low: 63.26,close: 64.4014,volume: 421766997},
    {x: new Date('2013-02-25'), open: 64.8357, high: 65.0171, low: 61.4257,close: 61.4957,volume: 582741215},
    {x: new Date('2013-03-04'), open: 61.1143, high: 62.2043, low: 59.8571,close: 61.6743,volume: 632856539},
    {x: new Date('2013-03-11'), open: 61.3928, high: 63.4614, low: 60.7343,close: 63.38,volume: 572066981},
    {x: new Date('2013-03-18'), open: 63.0643, high: 66.0143, low: 63.0286,close: 65.9871,volume: 552156035},
    {x: new Date('2013-03-25'), open: 66.3843, high: 67.1357, low: 63.0886,close: 63.2371,volume: 390762517},
    {x: new Date('2013-04-01'), open: 63.1286, high: 63.3854, low: 59.9543,close: 60.4571,volume: 505273732},
    {x: new Date('2013-04-08'), open: 60.6928, high: 62.57, low: 60.3557,close: 61.4,volume: 387323550},
    {x: new Date('2013-04-15'), open: 61, high: 61.1271, low: 55.0143,close: 55.79,volume: 709945604},
    {x: new Date('2013-04-22'), open: 56.0914, high: 59.8241, low: 55.8964,close: 59.6007,volume: 787007506},
    {x: new Date('2013-04-29'), open: 60.0643, high: 64.7471, low: 60,close: 64.2828,volume: 655020017},
    {x: new Date('2013-05-06'), open: 65.1014, high: 66.5357, low: 64.3543,close: 64.71,volume: 545488533},
    {x: new Date('2013-05-13'), open: 64.5014, high: 65.4143, low: 59.8428,close: 61.8943,volume: 633706550},
    {x: new Date('2013-05-20'), open: 61.7014, high: 64.05, low: 61.4428,close: 63.5928,volume: 494379068},
    {x: new Date('2013-05-27'), open: 64.2714, high: 65.3, low: 62.7714,close: 64.2478,volume: 362907830},
    {x: new Date('2013-06-03'), open: 64.39, high: 64.9186, low: 61.8243,close: 63.1158,volume: 443249793},
    {x: new Date('2013-06-10'), open: 63.5328, high: 64.1541, low: 61.2143,close: 61.4357,volume: 389680092},
    {x: new Date('2013-06-17'), open: 61.6343, high: 62.2428, low: 58.3,close: 59.0714,volume: 400384818},
    {x: new Date('2013-06-24'), open: 58.2, high: 58.38, low: 55.5528,close: 56.6471,volume: 519314826},
    {x: new Date('2013-07-01'), open: 57.5271, high: 60.47, low: 57.3171,close: 59.6314,volume: 343878841},
    {x: new Date('2013-07-08'), open: 60.0157, high: 61.3986, low: 58.6257,close: 60.93,volume: 384106977},
    {x: new Date('2013-07-15'), open: 60.7157, high: 62.1243, low: 60.5957,close: 60.7071,volume: 286035513},
    {x: new Date('2013-07-22'), open: 61.3514, high: 63.5128, low: 59.8157,close: 62.9986,volume: 395816827},
    {x: new Date('2013-07-29'), open: 62.9714, high: 66.1214, low: 62.8857,close: 66.0771,volume: 339668858},
    {x: new Date('2013-08-12'), open: 65.2657, high: 72.0357, low: 65.2328,close: 71.7614,volume: 711563584},
    {x: new Date('2013-08-19'), open: 72.0485, high: 73.3914, low: 71.1714,close: 71.5743,volume: 417119660},
    {x: new Date('2013-08-26'), open: 71.5357, high: 72.8857, low: 69.4286,close: 69.6023,volume: 392805888},
    {x: new Date('2013-09-02'), open: 70.4428, high: 71.7485, low: 69.6214,close: 71.1743,volume: 317244380},
    {x: new Date('2013-09-09'), open: 72.1428, high: 72.56, low: 66.3857,close: 66.4143,volume: 669376320},
    {x: new Date('2013-09-16'), open: 65.8571, high: 68.3643, low: 63.8886,close: 66.7728,volume: 625142677},
    {x: new Date('2013-09-23'), open: 70.8714, high: 70.9871, low: 68.6743,close: 68.9643,volume: 475274537},
    {x: new Date('2013-09-30'), open: 68.1786, high: 70.3357, low: 67.773,close: 69.0043,volume: 368198906},
    {x: new Date('2013-10-07'), open: 69.5086, high: 70.5486, low: 68.3257,close: 70.4017,volume: 361437661},
    {x: new Date('2013-10-14'), open: 69.9757, high: 72.7514, low: 69.9071,close: 72.6985,volume: 342694379},
    {x: new Date('2013-10-21'), open: 73.11, high: 76.1757, low: 72.5757,close: 75.1368,volume: 490458997},
    {x: new Date('2013-10-28'), open: 75.5771, high: 77.0357, low: 73.5057,close: 74.29,volume: 508130174},
    {x: new Date('2013-11-04'), open: 74.4428, high: 75.555, low: 73.1971,close: 74.3657,volume: 318132218},
    {x: new Date('2013-11-11'), open: 74.2843, high: 75.6114, low: 73.4871,close: 74.9987,volume: 306711021},
    {x: new Date('2013-11-18'), open: 74.9985, high: 75.3128, low: 73.3814,close: 74.2571,volume: 282778778},
];
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Months',
        valueType: 'DateTime',
        intervalType: 'Months',
        majorGridLines: { width: 0 },
        crosshairTooltip: { enable: true },
    },
    primaryYAxis: {
        title: 'Price (Million Dollars)',
        minimum: 30,
        maximum: 180,
        interval: 30,
    },
    axes: [{
        name: 'secondary',
        minimum: -7000000000, maximum: 5000000000,
        interval: 6000000000,
        majorGridLines: { width: 0 },
        opposedPosition: true
    }],
    indicators: [{
        type: 'AccumulationDistribution',
        dataSource : chartData, low: 'low', high: 'high', close: 'close', volume: 'volume',xName: 'x',
        yAxisName: 'secondary', fill: 'blue', open:'open'
        period: 3, animation: { enable: true }
    }],
    tooltip: { enable: true, shared: true },
    chartArea: { border: { width: 0 } },
    axisLabelRender: (args: IAxisLabelRenderEventArgs) => {
            if (args.axis.name === 'secondary') {
                let value: number = Number(args.text) / 1000000000;
                args.text = String(value) + 'bn';
            }
        },
    crosshair: { enable: true, lineType: 'Vertical' },
    title: 'AAPL - 2016/2017'
}, '#element');

```

{% endtab %}