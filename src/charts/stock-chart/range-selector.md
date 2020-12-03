---
title: " StockChart Selecting Range | TypeScript "

component: "StockChart"

description: "we can able to select the particular range data by dragging thumbs or by tapping on the labels or by setting the start and end value properties. "
---

# Selecting Range

The left and right thumb of RangeNavigator are used to indicate the selected range in the large collection of data. Following are the ways you can select a range.

* By dragging the thumbs.
* By tapping on the labels.
* By setting the start and end through Date Range button.

Following code example shows the [`enableSelector`](../api/stock-chart/stockChartModel/#enableselector) property allows users to toggle the visibility of range selector.

{% tab template= "stock-chart/getting-started", es5Template="es5VisibilityRange" %}

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
       enableSelector : false,
       primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent', width: 0 },
        },
        primaryXAxis: { majorGridLines: { color: 'transparent' }},
        series: [
            {
                dataSource: chartData,
                type: 'Candle'
            },
        ],
        title: 'AAPL Stock Price'
});
stockChart.appendTo('#element');
```

{% endtab %}
