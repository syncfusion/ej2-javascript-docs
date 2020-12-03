---
title: " Stock Chart Crosshair | TypeScript "

component: "StockChart"

description: "Crosshair has a vertical and horizontal line to view the value of the axis at mouse position.The trackball used to display data collections"
---

# Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairSettingsModel/#enable) property in the `crosshair`.

{% tab template= "stock-chart/getting-started", es5Template="es5CrossHair" %}

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
       crosshair: {
            enable: true
        },
        title: 'AAPL Stock Price'
});
stockChart.appendTo('#element');

```

{% endtab %}

## Tooltip for axis

Tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel/#enable) property of `crosshairTooltip` in the corresponding axis.

{% tab template= "stock-chart/getting-started", es5Template="es5CrossHair" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);
import { chartData } from './datasource.ts';

let stockChart: StockChart = new StockChart({
       primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent', width: 0 },
            crosshairTooltip: {enable:true}
        },
        primaryXAxis: { majorGridLines: { color: 'transparent' },
        crosshairTooltip: {enable:true}},
        series: [
            {
                dataSource: chartData,
                type: 'Candle'
            }
        ],
       crosshair: {
            enable: true
        },
        title: 'AAPL Stock Price'
});
stockChart.appendTo('#element');

```

{% endtab %}

## Customization

The [`fill`](../api/chart/crosshairTooltipModel/#fill) and [`textStyle`](../api/chart/crosshairTooltipModel/#textstyle)
property of the `crosshairTooltip` is used to customize the background color and font style of the crosshair label respectively.
Color and width of the crosshair line can be customized by using the
[`line`](../api/chart/crosshairSettingsModel/#line) property in the crosshair.

{% tab template= "stock-chart/getting-started", es5Template="es5CrossHairCus" %}

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
       primaryYAxis: {
            lineStyle: { color: 'transparent' },
            majorTickLines: { color: 'transparent', width: 0 },
            crosshairTooltip: {enable:true,fill: 'green'}
        },
        primaryXAxis: { majorGridLines: { color: 'transparent' },
        crosshairTooltip: {enable:true,fill: 'green'}},
        series: [
            {
                dataSource: chartData,
                type: 'Candle'
            }
        ],
       crosshair: {
            enable: true,
            line: {width: 2, color: 'green'}
        },
        title: 'AAPL Stock Price'
});
stockChart.appendTo('#element');
```

{% endtab %}

>Note: To use crosshair feature, we need to inject `Crosshair` module `StockChart.Inject(Crosshair)` method.
