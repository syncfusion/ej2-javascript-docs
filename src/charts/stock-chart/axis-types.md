---
title: " Stock Chart Axis Types | TypeScript "

component: "Stock Chart"

description: "Date time axis uses date time scale and displays the date time values as axis labels in the specified format. "
---
<!-- markdownlint-disable MD036 -->

# DateTime,Numeric and Logarithmic Axis

## DateTime Axis

Date time axis uses date time scale and displays the date time values as axis labels in the specified format. and
set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to DateTime.

{% tab template= "stock-chart/getting-started", es5Template="es5DateTime" %}

```typescript
import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair }
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
  primaryXAxis: { valueType: 'DateTime' },
  series: [
    {
      dataSource: chartData,
      type: 'Candle'
    },
  ],

});
stockChart.appendTo('#element');

```

{% endtab %}

>Note: To use datetime axis, we need to inject DateTime using `StockChart.Inject(DateTime)` method and
set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to DateTime.

## Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic axis uses logarithmic scale and it is very useful in visualizing data, when it has numerical values in
both lower order of magnitude (eg: 10<sup>-6</sup>) and higher order of magnitude (eg: 10<sup>6</sup>).
and
set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to `Lograthmic`.

{% tab template= "stock-chart/getting-started", es5Template= "es5LogAxis" %}

```typescript
import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime,AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries ,Logarithmic } from '@syncfusion/ej2-charts';
import { SplineAreaSeries, SplineSeries  } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime,Logarithmic,  AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineAreaSeries, SplineSeries );
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

    let stockChart: StockChart = new StockChart({
        primaryXAxis: { valueType: 'DateTime' },
        primaryYAxis: {
               valueType: 'Logarithmic'
        },
        chartArea: { border: { width: 0 } },
        series: [
            {
                dataSource: chartData, type: 'Line' xName: 'date' yName: 'high'
            }
        ],

    });
    stockChart.appendTo('#element');

```

{% endtab %}

>Note: To use log axis, we need to inject `Logarithmic` using method `StockChart.Inject(Logarithmic)` and
set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) of axis to `Logarithmic`.

## See Also

* [Axis Customization](./axis-customization/)