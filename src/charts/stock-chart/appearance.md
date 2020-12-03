---
title: " Stock Chart Appearance | TypeScript "

component: "StockChart"

description: "We can customize stock chart appearance by using title and tooltip customizations."
---

# Appearance

## Stock Chart Title

Stock Chart can be given a title using [`title`](../api/stock-chart/#title) property, to show the information
about the data plotted.

{% tab template= "stock-chart/getting-started", es5Template="es5Title" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair} from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);
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
        title: 'AAPL Stock Price',
         titleStyle:{
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '20px'
        }
});
stockChart.appendTo("#element");
```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**Title Customization**

The `textStyle` property of stock chart title provides options to customize the `size`, `color`, `fontFamily`, `fontWeight`, `fontStyle`, `opacity`, `textAlignment` and `textOverflow`.

{% tab template= "stock-chart/getting-started", es5Template= "es5TitleWrap" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Crosshair, IStockChartEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
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
        title: 'AAPL Stock Price',
         titleStyle:{
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '20px',
             textOverflow: 'Wrap'
        }
});
stockChart.appendTo("#element");
```

{% endtab %}

## Stock Chart Theme

Changing Stock Chart theme will affect background color, grid lines, tooltip colors and appearance.

[`theme`](../api/stock-chart/stockChartModel/#theme) property of Stock chart is shipped with several built-in themes such as `Material`, `Fabric`, `Bootstrap` , `HighContrastLight`, `MaterialDark`, `FabricDark`, `FabricDark`, `HighContrast` and `BootstrapDark`.

{% tab template= "stock-chart/theme", es5Template="es5Theme" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Crosshair} from '@syncfusion/ej2-charts';
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
        title: 'AAPL Stock Price',
        theme:'HighContrast'
});
stockChart.appendTo("#element");
```

{% endtab %}

## See Also

* [Axis Customization](./axis-customization/)