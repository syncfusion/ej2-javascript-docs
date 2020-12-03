---
title: " Stock Chart Appearance | TypeScript "

component: "Stock Chart"

description: "We can set Stock Chart size manually by using width and height properties. We can set percentage or pixel size values to the Stock Chart."
---

# Stock Chart Dimensions

## Size for Container

Stock Chart can render to its container size. You can set the size via inline or CSS as demonstrated below.

{% tab template= "stock-chart/chart-dimensions", es5Template="es5Dimensions" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, CandleSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair}
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, CandleSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
  series: [
    {
      dataSource: chartData,
      type: 'Candle'
    },
  ]
});
stockChart.appendTo('#element');
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Size for Stock Chart

<!-- markdownlint-disable MD036 -->

You can also set size for chart directly through [`width`](../api/stock-chart/#width) and [`height`](../api/stock-chart/#height) properties.

**In Pixel**

You can set the size of chart in pixel as demonstrated below.

{% tab template= "stock-chart/chart-dimensions", es5Template="es5chartSize" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, CandleSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair}
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, CandleSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
  series: [
    {
      dataSource: chartData,
      type: 'Candle'
    },
  ],
    // Width and height for stock chart in pixel
    width: '650', height: '350'

});
stockChart.appendTo('#element');

```

{% endtab %}

**In Percentage**

By setting value in percentage, Stock Chart gets its dimension with respect to its container. For example, when
the height is ‘50%’, Stock Chart renders to half of the container height.

{% tab template= "stock-chart/chart-dimensions", es5Template="es5ChartSizePercent" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, CandleSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair}
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, CandleSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
  series: [
    {
      dataSource: chartData,
      type: 'Candle'
    },
  ],
  // Width and height for stock chart in percentage
    width: '80%', height: '90%'

});
stockChart.appendTo('#element');
```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.