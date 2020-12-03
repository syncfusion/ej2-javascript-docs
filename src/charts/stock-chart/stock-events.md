---
title: " Stock Events | TypeScript "
component: "Stock Chart"
description: "Stock Chart can be rendered by using different types of data source. They are called local data, remote data and empty points. "
---

<!-- markdownlint-disable MD036 -->

# Stock Events

Stock Events visualizes stock events in stock chart. 'SplineSeries' is used to represent selected data value. You can customize the specific data value using `stockEvents` event.

{% tab template= "stock-chart/getting-started", es5Template="es5StockEvents" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair , IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

 let stockChart: StockChart = new StockChart({
 chartArea: { border: { width: 0 } },
        primaryXAxis: { valueType: 'DateTime', majorGridLines: { color: 'transparent' }, crosshairTooltip: { enable: true } },
        primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent' },
            crosshairTooltip: { enable: true }
        },
        series: [
            {
                dataSource: chartData, xName: 'date', yName: 'high', type: 'Spline'
            }
        ],
        stockEvents: [
            { date: new Date(2012, 3, 1), text: 'Q2', description: '2012 Quarter2 starts', type: 'Flag', background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2012, 3, 20), text: 'Open', description: 'Markets opened', textStyle: { color: 'white' },
              background: '#f48a21', border: { color: '#f48a21' } },
            { date: new Date(2012, 6, 1), text: 'Q3', description: '2013 Quarter3 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2012, 9, 1), text: 'Q4', description: '2013 Quarter4 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2012, 7, 30), text: 'G', description: 'Google stocks bought',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' } },
            { date: new Date(2012, 10, 1), text: 'Y', description: 'Yahoo stocks sold', type: 'Square',
              textStyle: { color: 'white' }, background: '#841391', border: { color: '#841391' } },
            { date: new Date(2012, 12, 0), text: 'Y2', description: 'Year 2013', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' } },
            { date: new Date(2013, 3, 1), text: 'Q2', description: '2013 Quarter2 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2013, 3, 20), text: 'Q2', description: 'Surge in Stocks', type: 'ArrowUp',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' } },
            { date: new Date(2013, 6, 1), text: 'Q3', description: '2013 Quarter3 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2013, 9, 1), text: 'Q4', description: '2013 Quarter4 starts',  type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2013, 12, 0), text: 'Y3', description: 'Year 2014', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' } },
            { date: new Date(2014, 3, 1), text: 'Q2', description: '2014 Quarter2 starts', type: 'ArrowDown',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' } },
            { date: new Date(2014, 6, 1), text: 'Q3', description: '2014 Quarter3 starts',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' } },
            { date: new Date(2014, 9, 1), text: 'Q4', description: '2014 Quarter4 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' } },
            { date: new Date(2014, 12, 0), text: 'Y4', description: 'Year 2015', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' } },
            { date: new Date(2014, 2, 2), text: 'End', description: 'Markets closed', type: 'ArrowDown',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' } },
            { date: new Date('2015-01-07'), text: 'A', description: 'This is event description',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' } },
            { date: new Date(2015, 1, 2), text: 'Q1', description: 'Add longer text',
              textStyle: { color: 'white' }, background: '#dd3c9f', border: { color: '#dd3c9f' }, type: 'Text' },
            { date: new Date(2015, 2, 12), text: 'Close', description: 'Markets closed',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' } }
        ],
        seriesType : [],
        indicatorType : [],
        trendlineType: [],
        title: 'AAPL Stock Price',
        crosshair: { enable: true },
      });
      stockChart.appendTo('#element');
```

{% endtab %}

**Stock Events for individual series**

By default, stock events will be showed for all series. Now, you can set the stock events for particular series using `seriesIndexes` property.

{% tab template= "stock-chart/getting-started", es5Template="es5StockEventsSingle" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair , IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

 let stockChart: StockChart = new StockChart({
 chartArea: { border: { width: 0 } },
        primaryXAxis: { valueType: 'DateTime', majorGridLines: { color: 'transparent' }, crosshairTooltip: { enable: true } },
        primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent' },
            crosshairTooltip: { enable: true }
        },
        series: [
            {
                dataSource: chartData, xName: 'date', yName: 'high', type: 'Spline'
            },
            {
                dataSource: chartData, xName: 'date', yName: 'low', type: 'Spline'
            },
            {
                dataSource: chartData, xName: 'date', yName: 'open', type: 'Spline'
            }
        ],
        stockEvents: [
            { date: new Date(2012, 3, 1), text: 'Q2', description: '2012 Quarter2 starts', type: 'Flag', background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [0] },
            { date: new Date(2012, 3, 20), text: 'Open', description: 'Markets opened', textStyle: { color: 'white' },
              background: '#f48a21', border: { color: '#f48a21' }, seriesIndexes: [0] },
            { date: new Date(2012, 6, 1), text: 'Q3', description: '2013 Quarter3 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [0] },
            { date: new Date(2012, 9, 1), text: 'Q4', description: '2013 Quarter4 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [0] },
            { date: new Date(2012, 7, 30), text: 'G', description: 'Google stocks bought',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' }, seriesIndexes: [0] },
            { date: new Date(2012, 10, 1), text: 'Y', description: 'Yahoo stocks sold', type: 'Square',
              textStyle: { color: 'white' }, background: '#841391', border: { color: '#841391' }, seriesIndexes: [0] },
            { date: new Date(2012, 12, 0), text: 'Y2', description: 'Year 2013', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' }, seriesIndexes: [0] },
            { date: new Date(2013, 3, 1), text: 'Q2', description: '2013 Quarter2 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [0] },
            { date: new Date(2013, 3, 20), text: 'Q2', description: 'Surge in Stocks', type: 'ArrowUp',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' }, seriesIndexes: [1] },
            { date: new Date(2013, 6, 1), text: 'Q3', description: '2013 Quarter3 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [1] },
            { date: new Date(2013, 9, 1), text: 'Q4', description: '2013 Quarter4 starts',  type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [1] },
            { date: new Date(2013, 12, 0), text: 'Y3', description: 'Year 2014', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' }, seriesIndexes: [1] },
            { date: new Date(2014, 3, 1), text: 'Q2', description: '2014 Quarter2 starts', type: 'ArrowDown',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' }, seriesIndexes: [1] },
            { date: new Date(2014, 6, 1), text: 'Q3', description: '2014 Quarter3 starts',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' }, seriesIndexes: [2] },
            { date: new Date(2014, 9, 1), text: 'Q4', description: '2014 Quarter4 starts', type: 'Flag',
              textStyle: { color: 'white' }, background: '#6c6d6d', border: { color: '#6c6d6d' }, seriesIndexes: [2] },
            { date: new Date(2014, 12, 0), text: 'Y4', description: 'Year 2015', type: 'Pin', showOnSeries: false,
              textStyle: { color: 'white' }, background: '#6322e0', border: { color: '#6322e0' }, seriesIndexes: [2] },
            { date: new Date(2014, 2, 2), text: 'End', description: 'Markets closed', type: 'ArrowDown',
              textStyle: { color: 'white' }, background: '#3ab0f9', border: { color: '#3ab0f9' }, seriesIndexes: [2] },
            { date: new Date('2015-01-07'), text: 'A', description: 'This is event description',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' }, seriesIndexes: [2] },
            { date: new Date(2015, 1, 2), text: 'Q1', description: 'Add longer text',
              textStyle: { color: 'white' }, background: '#dd3c9f', border: { color: '#dd3c9f' }, type: 'Text', seriesIndexes: [2] },
            { date: new Date(2015, 2, 12), text: 'Close', description: 'Markets closed',
              textStyle: { color: 'white' }, background: '#f48a21', border: { color: '#f48a21' }, seriesIndexes: [2] }
        ],
        seriesType : [],
        indicatorType : [],
        trendlineType: [],
        title: 'AAPL Stock Price',
        crosshair: { enable: true },
      });
      stockChart.appendTo('#element');
```

{% endtab %}

## See Also

* [Series Types](./series-types/)