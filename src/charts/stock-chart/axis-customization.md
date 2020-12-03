---
title: " Stock Chart Axis Customization | TypeScript "

component: "Stock Chart"

description: " Stock Chart axis contains different customization and types like axis crossing, multiple axis, inversed axis, tick and grid, title customizations"
---

# Axis Customization

## Axis Crossing

An axis can be positioned in the Stock Chart area using [`crossesAt`](../api/stock-chart/stockChartAxisModel/#crossesat) and [`crossesInAxis`] (../api/stock-chart/stockChartAxisModel/#crossesinaxis) properties. The [`crossesAt`](../api/stock-chart/stockChartAxisModel/#crossesat) property specifies the values (datetime, numeric, or logarithmic) at which the axis line has to be intersected with the vertical axis or vice-versa, and the [`crossesInAxis`](../api/stock-chart/stockChartAxisModel/#crossesinaxis) property specifies the axis name with which the axis line has to be crossed.

{% tab template= "stock-chart/getting-started", es5Template="es5AxisPosition" %}

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
  primaryXAxis: {
    crossesAt: 90
  },
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

## Title

You can add a title to the axis using [`title`](../api/stock-chart/stockChartAxisModel/#title) property to provide quick
information to the user about the data plotted in the axis. Title style can be customized using [`titleStyle`](../api/stock-chart/stockChartAxisModel/#titlestyle) property of the axis.

{% tab template= "stock-chart/getting-started", es5Template="es5AxisTitle" %}

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
  primaryXAxis: {

    title: 'AAPL Historical',
  },
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

## Tick Lines Customization

You can customize the  `width`, `color` and `size` of the minor and major tick lines, using
[`majorTickLines`](../api/stock-chart/stockChartAxisModel/#majorticklines) and
[`minorTickLines`](../api/stock-chart/stockChartAxisModel/#minorticklines) properties in the axis.

{% tab template= "stock-chart/getting-started", es5Template="es5TickLines" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs }
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
  primaryXAxis: {

   //Tick lines customization
        majorTickLines : {
            color : 'blue',
            width : 5
        },
        minorTickLines : {
            color : 'red',
            width : 0
        }
  },
     primaryYAxis: {
    //Grid lines customization
        majorTickLines : {
            color : 'green',
            width : 5
        },
        minorTickLines : {
            color : 'red',
            width : 0
        },
     },
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

## Grid Lines Customization

You can customize the `width`, `color` and `dashArray` of the minor and major grid lines, using [`majorGridLines`](../api/stock-chart/stockChartAxisModel/#majorgridlines)
and [`minorGridLines`](../api/stock-chart/stockChartAxisModel/#minorgridlines) properties in the axis.

{% tab template= "stock-chart/getting-started", es5Template="es5GridLines" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs }
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
 primaryXAxis: {
        //Grid lines customization
        majorGridLines : {
            color : 'blue',
            width : 1
        },
        minorGridLines : {
            color : 'red',
            width : 0
        }
    },
    primaryYAxis: {
        //Grid lines customization
        majorGridLines : {
            color : 'green',
            width : 1
        },
        minorGridLines : {
            color : 'red',
            width : 0
        }
    },
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

## Multiple Axis

In addition to primary X and Y axis, we can add n number of axis to the Stock Chart. Series can be associated with
this [`axis`](../api/stock-chart/stockChartAxisModel), by mapping with axis's unique name.

{% tab template= "stock-chart/getting-started", es5Template="es5MultipleAxis" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, LineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair}
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, LineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

 let stockChart: StockChart = new StockChart({
        series: [
            {
                dataSource: chartData, type: 'Line', xName: 'date' yName: 'high'
            },
            {
                dataSource: chartData, type: 'Line', xName: 'date' yName: 'low'
                 yAxisName: 'yAxis',
            }
        ],
         // Initializing multiple axis
       axes:[
        {
            rowIndex: 0,
            name: 'yAxis',
        }
       ],
        crosshair: {
            enable: true
        },
        title: 'Multiple Axis',

    });

stockChart.appendTo('#element');

```

{% endtab %}

## Inversed Axis

<!-- markdownlint-disable MD033 -->

When an axis is inversed, highest value of the axis comes closer to origin and vice versa. To place an axis in inversed manner set this property
 [`isInversed`](../api/stock-chart/stockChartAxisModel/#isinversed) to true.

{% tab template= "stock-chart/getting-started", es5Template="es5InversedAxis" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs }
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({
        //Initializing Primary X Axis
        primaryXAxis: {
             isInversed: true
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
             isInversed: true
        },
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

## Opposed Position

To place an axis opposite from its original position,
set [`opposedPosition`](../api/stock-chart/stockChartAxisModel/#opposedposition) property of the axis to true.

{% tab template= "stock-chart/getting-started", es5Template="es5OpposedAxis" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs }
  from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export);

let stockChart: StockChart = new StockChart({

  primaryXAxis:
  {
    opposedPosition: true
  },
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