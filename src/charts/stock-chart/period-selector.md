---
title: " Stock Chart Period Selector | TypeScript "

component: "StockChart"

description: "The period selector allows to select a range with specified periods."
---

# Period selector

The period selector allows to select a range with specified periods. By default the period selector is enabled in stock chart.

## Periods

Periods is an array of objects that allows users to specify the range of [`periods`](../api/stock-chart/stockChartModel/#periods). The `interval` property specifies the count value of the button, and the `text` property specifies the text to be displayed on button. The `intervalType` property allows users to customize the intervals of the buttons. The `intervalType` property supports the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template= "stock-chart/getting-started", es5Template="es5PeriodSelector" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, Export,SplineSeries } from '@syncfusion/ej2-charts';
import { RangeTooltip, Crosshair } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(RangeTooltip, Crosshair, Export);

    let stockChart: StockChart = new StockChart({
        primaryXAxis: { valueType: 'DateTime', majorGridLines: { color: 'transparent' },
                        crosshairTooltip: { enable: true } },
        primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent', width: 0 },
            crosshairTooltip: { enable: true }
        },
       series: [
            {
                dataSource: GetDateTimeData(), xName: 'x', yName: 'y', type: 'Line', name: 'google',
            }
        ],
        seriesType: [],
        indicatorType: [],
        exportType: [],
        trendlineType : [],
        periods: [
            { intervalType: 'Minutes', interval: 1, text: '1m' },
            { intervalType: 'Minutes', interval: 30, text: '30m' },
            { intervalType: 'Hours', interval: 1, text: '1H' },
            { intervalType: 'Hours', interval: 12, text: '12H', selected: true },
            { text: '1D' }
        ],
        title: 'AAPL stock price by minutes',
        crosshair: {
            enable: true
        },
});
stockChart.appendTo('#element');

function GetDateTimeData() : {x: Date, y: number}[]{
       let series1: Object[] = [];
    let point1: Object;
    let value: number = 80;
    let i: number;
    for (i = 1; i < 500; i++) {
        if (Math.random() > .5) {
            value += Math.random();
        } else {
            value -= Math.random();
        }
        point1 = { x: new Date(2000, 1, 1, 0, i), y: value.toFixed(1) };
        series1.push(point1);
    }
    return series1;
}

```

{% endtab %}

## Visibility of period selector

The [`enablePeriodSelector`](../api/stock-chart/stockChartModel/#enableperiodselector) property allows users to toggle the visibility of period selector.

{% tab template= "stock-chart/getting-started", es5Template="es5VisibilityPeriod" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Crosshair } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Crosshair, Export);
import { chartData } from './datasource.ts';

let stockChart: StockChart = new StockChart({
        enablePeriodSelector: false,
        primaryXAxis: { valueType: 'DateTime', majorGridLines: { color: 'transparent' },
                        crosshairTooltip: { enable: true } },
        primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent', width: 0 },
            crosshairTooltip: { enable: true }
        },
        series: [
            {
                dataSource: chartData, type: 'Candle', name: 'google',
            }
        ],
        title: 'AAPL stock price by minutes',
        crosshair: {
            enable: true
        }
});
stockChart.appendTo('#element');

```

{% endtab %}