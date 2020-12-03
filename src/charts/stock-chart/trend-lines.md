---
title: " StockChart Trendlines | TypeScript "

component: "StockChart"

description: "Trendlines are used to show the direction and speed of price. StockChart supports 6 types of trendlines and also provides trendlines customization."
---
<!-- markdownlint-disable MD036 -->

# Trendlines

Trendlines are used to show the direction and speed of price.

StockChart supports 6 types of trendlines namely `Linear`,`Exponential`,`Logarithmic`,`Polynomial`,`Power`,`Moving Average`. By using trendline dropdown button you can add or remove the required trendline type.

## Linear

A linear trendline is a best fit straight line that is used with simpler data sets. To render a linear trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Linear` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

## Exponential

An exponential trendline is a curved line that is most useful when data values rise or fall at increasingly higher rates. You cannot create an exponential trendline, if your data contains zero or negative values.

To render a exponential trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Exponential` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

## Logarithmic

A logarithmic trendline is a best-fit curved line that is most useful when the rate of change in the data increases or decreases quickly and then levels out. A logarithmic trendline can use negative and/or positive values.

To render a logarithmic trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Logarithmic` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

## Polynomial

A polynomial trendline is a curved line that is used when data fluctuates.

To render a polynomial trendline,
use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Polynomial` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

`polynomialOrder` used to define the polynomial value.

## Power

A power trendline is a curved line that is best used with data sets that compare measurements that increase at a specific rate.

To render a power trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `Power` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

## Moving Average

A moving average trendline smoothen out fluctuations in data to show a pattern or trend more clearly.

To render a moving average trendline, use trendline [`type`](../api/stock-chart/stockChartTrendlineModel/#type) as `MovingAverage` and inject
`Trendlines` module using `StockChart.Inject(Trendlines)`.

`period` property defines the period to find the moving average.

{% tab template= "stock-chart/getting-started", es5Template="es5MovingAverage" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime,AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries ,Logarithmic } from '@syncfusion/ej2-charts';
import { SplineAreaSeries, SplineSeries  } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
StockChart.Inject(DateTime,Logarithmic,  AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineAreaSeries, SplineSeries );
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
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
        dataSource: chartData,
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as candle
        type: 'Candle',
        trendlines: [{ type: 'MovingAverage', enableTooltip:false }]
    }],
    seriesType: [],
    indicatorType: [],
    exportType: [],
    title: 'Historical Indian Rupee Rate (INR USD)'
});
stockChart.appendTo('#element');
```

{% endtab %}

**Customization of Trendline**

The [`fill`](../api/stock-chart/stockChartTrendlineModel/#fill) and [`width`](../api/stock-chart/stockChartTrendlineModel/#width) properties are used to customize the appearance of the trendline.

{% tab template= "stock-chart/getting-started", es5Template="es5TrendlineCust" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime,AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries ,Logarithmic } from '@syncfusion/ej2-charts';
import { SplineAreaSeries, SplineSeries  } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
StockChart.Inject(DateTime,Logarithmic,  AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineAreaSeries, SplineSeries );
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
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
        dataSource: chartData,
        name: 'Apple Inc',
        fill: '#0066FF',
        //Series type as candle
        type: 'Candle',
        trendlines: [{ type: 'MovingAverage', enableTooltip:false, fill: 'red', width:2 }]
    }],
    seriesType: [],
    indicatorType: [],
    exportType: [],
    title: 'Historical Indian Rupee Rate (INR USD)'
});
stockChart.appendTo('#element');

```

{% endtab %}