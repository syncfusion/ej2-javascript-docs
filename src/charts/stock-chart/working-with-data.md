---
title: " Stock Chart Working With Data | TypeScript "

component: "Stock Chart"

description: "Stock Chart can be rendered by using different types of data source. They are called local data, remote data and empty points. "
---
<!-- markdownlint-disable MD036 -->

# Working with Data

Stock Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/stock-chart/stockSeriesModel/#datasource) property in series.

{% tab template= "stock-chart/working-with-data", es5Template="es5LocalData" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, HiloOpenCloseSeries, CandleSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair}
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, HiloOpenCloseSeries, CandleSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

 let stockChart: StockChart = new StockChart({
        series: [
            {
                dataSource: chartData, type: 'Candle',
                animation: { enable: true },
                bearFillColor: '#2ecd71', bullFillColor: '#e74c3d',
            }
        ],
        });
    stockChart.appendTo("#element");

```

{% endtab %}

## See Also

* [Series Types](./series-types/)