---
title: " Series Types | TypeScript "

component: "StockChart"

description: "Essential JS 2 StockChart  StockChart supports 32 types of series and also supports different tpes customizations for each type of StockChart."
---

# StockChart Series Types

Essential JS 2 StockChart supports 6 major types of series namely `Line`, `Spline`, `Hilo`, `HiloOpenClose`, `Hollow Candle` and `Candle` . By using the series dropdown button you can navigate between the above listed series types.

<!-- markdownlint-disable MD036 -->

## Line

To render a line series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Line` and
inject `LineSeries` module using `StockChart.Inject(LineSeries)` method.

## Spline

To render a spline series, use series [`type`](../api/stock-chart/stockSeriesModel/#type-string) as `Spline` and
inject `SplineSeries` module using `StockChart.Inject(SplineSeries)` method.

## Hilo

To render a hilo series, use series [`type`](../api/stock-chart/stockSeriesModel/#type) as `Hilo` and
inject `HiloSeries` module using `StockChart.Inject(HiloSeries)` method.

## HiloOpenClose

To render a hiloOpenClose series, use series [`type`](../api/stock-chart/stockSeriesModel/#type) as `HiloOpenClose` and
inject `HiloOpenCloseSeries` module using `StockChart.Inject(HiloOpenCloseSeries)` method.

## HollowCandle

To render a hollowcandle series, use series [`type`](../api/stock-chart/stockSeriesModel/#type) as `Candle` and set `enableSolidCandle` as false. Now inject `CandleSeries` module using `StockChart.Inject(CandleSeries)` method.

## Candle

To render a candle series, use series [`type`](../api/stock-chart/stockSeriesModel/#type) as `Candle` and
inject `CandleSeries` module using `StockChart.Inject(CandleSeries)` method.

{% tab template= "stock-chart/getting-started", es5Template="es5Candle" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { RangeTooltip, Tooltip, Crosshair }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject( RangeTooltip, Tooltip, Crosshair);

let stockChart: StockChart = new StockChart({

series:[{
    dataSource: chartData,
    type: 'Candle'
}],
indicatorType: [];
trendlineType: [];
exportType: [];
});
stockChart.appendTo('#element');
```

{% endtab %}
