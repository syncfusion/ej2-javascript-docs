---
title: " StockChart Tooltip | TypeScript "

component: "StockChart"

description: "Tooltip is used to show the data value when mouse hover on the stockchart.We can able to customize format,template and appearance."
---

# Tooltip

<!-- markdownlint-disable MD036 -->

StockChart will display details about the points through tooltip, when the mouse is moved over the point.

## Default Tooltip

By default, tooltip is not visible. Enable the tooltip by setting
[`enable`](../api/chart/tooltipSettings/#enable) property to true and by injecting [`Tooltip`](../api/stock-chart/stockChartModel/#tooltip) module
using `StockChart.Inject(Tooltip)`.

{% tab template= "stock-chart/getting-started", es5Template="es5Tooltip" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        series: [
            {
                type: 'Candle',
                dataSource: chartData
            }],
        title: 'Unemployment Rates 1975-2010',
        //Default tooltip for StockChart
        tooltip: {enable: true}
});
stockChart.appendTo('#element');
```

{% endtab %}

<!-- markdownlint-disable MD013 -->

## Format the Tooltip

<!-- markdownlint-disable MD013 -->

By default, tooltip shows information of x and y value in points. In addition to that, you can show more information in tooltip. For example the format `${series.name} ${point.x}` shows series name and point x value.

{% tab template= "stock-chart/getting-started", es5Template="es5FormatTooltip" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        series: [
            {
                type: 'Candle',
                dataSource: chartData
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            //tooltip format for StockChart
             header: 'Unemployment',
             format: '<b>${point.x} : ${point.y}</b>'
        }
});
stockChart.appendTo('#element');
```

{% endtab %}

## Customize the Appearance of Tooltip

The [`fill`](../api/chart/tooltipSettingsModel/#fill) and [`border`](../api/chart/tooltipSettingsModel/#border) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](../api/chart/tooltipSettingsModel/#textStyle) property in the tooltip is used to customize the font of the tooltip text.

{% tab template= "stock-chart/getting-started", es5Template="es5ApperanceTooltip" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Candle',
                dataSource: chartData
            }
        ],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            format: ' ${point.x} : ${point.y}',
            //fill for tooltip
            fill: '#7bb4eb',
            //border for tooltip
            border: {
                width: 2,
                color: 'grey'
            }
        }
});
stockChart.appendTo('#element');

```

{% endtab %}
