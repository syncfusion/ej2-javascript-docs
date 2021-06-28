---
title: " Stock Chart Legend | TypeScript "

component: "Stock Chart"

description: "Stock Chart legend provides information about the series rendered in the Stock Chart. It has different alignment, shapes and customization properties. "
---

<!-- markdownlint-disable MD036 -->

# Legend

<!-- markdownlint-disable MD038 -->

Legend provides information about the series rendered in the Stock Chart. Legend can be added to a Stock Chart by enabling the [`visible`](../api/stock-chart/legendSettings/#visible) option in the [`legendSettings`](../api/stock-chart/legendSettings/).

## Position and Alignment

By using the [`position`](../api/stock-chart/legendSettings/#position) property, legend can be placed at `Left`, `Right`, `Top`, `Bottom` or `Custom` of the Stock Chart. The legend is positioned at the bottom of the Stock Chart, by default.

{% tab template= "stock-chart/legend", es5Template="es5StockLegend" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
        visible: true,
        //Legend position as top
        position:'Top'
        }
});
stockChart.appendTo('#element');
```

{% endtab %}

[`Custom`](../api/stock-chart/legendSettings/#position) position is used to position the legend anywhere in the Stock Chart using x, y coordinates.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendPosition" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
        visible: true,
        //Legend position as custom
        position:'Custom',
        location: { x: 200, y: 20 } }
});
stockChart.appendTo('#element');
```

{% endtab %}

**Legend Alignment**

The legend can be align as `Center`, `Far` or `Near` to the Stock Chart using [`alignment`](../api/stock-chart/legendSettings/#alignment) property.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendAlignment" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
        visible: true,
        position:'Bottom',
        //Legend alignment as near
        alignment: 'Near'
        }
});
stockChart.appendTo('#element');
```

{% endtab %}

## Customization

To change the legend icon shape, [`legendShape`](../api/stock-chart/stockSeries/#legendshape-string) property in the [`series`](../api/stock-chart/stockSeries/) can be used. By default legend icon shape is `seriesType`.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendCust" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China',
                legendShape: 'Pentagon'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: { visible: true }
});
stockChart.appendTo('#element');
```

{% endtab %}

**Legend Size**

By default, legend takes 20% - 25% of the Stock Chart's height horizontally, when it is placed on top or bottom position and 20% - 25% of the width vertically, while placing on left or right position of the Stock Chart. The default legend size can be changed by using the [`width`](../api/stock-chart/legendSettings/#width) and [`height`](../api/stock-chart/legendSettings/#height) property of the `legendSettings`.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendSize" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
        visible: true,
        //Legend size for chart
        width: '500', height: '50',
        border: { width: 1, color: 'pink'}
        }
});
stockChart.appendTo('#element');
```

{% endtab %}

**Legend Item Size**

The size of the legend items can customized by using the [`shapeHeight`](../api/stock-chart/legendSettings/#shapeheight) and [`shapeWidth`](../api/stock-chart/legendSettings/#shapewidth) property.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendItemSize" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
        visible: true,
        //Legend item size for chart
        shapeHeight: 15, shapeWidth: 15
        }
});
stockChart.appendTo('#element');

```

{% endtab %}

## Collapsing Legend Item

By default, series name will be displayed as legend. To skip the legend for a particular series, empty string to the series name can be given.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendCollapse" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: { visible: true }
});
stockChart.appendTo('#element');
```

{% endtab %}

## Legend Title

The title for legend can be set using [`title`](../api/stock-chart/legendSettings/#title) property in `legendSettings`. Customize the [`fontStyle`](../api/stock-chart/stockChartFont/#fontstyle), [`size`](../api/stock-chart/stockChartFont/#size), [`fontWeight`](../api/stock-chart/stockChartFont/#fontweight), [`color`](../api/stock-chart/stockChartFont/#color), [`textAlignment`](../api/stock-chart/stockChartFont/#textalignment), [`fontFamily`](../api/stock-chart/stockChartFont/#fontfamily), [`opacity`](../api/stock-chart/stockChartFont/#opacity) and [`textOverflow`](../api/stock-chart/stockChartFont/#textoverflow) of legend title. [`titlePosition`](../api/stock-chart/legendSettings/#titleposition) is used to set the legend position in `Top`, `Left` and `Right` position. [`maximumTitleWidth`](../api/stock-chart/legendSettings/#maximumtitlewidth) is used to set the width of the legend title. By default, it will be `100px`.

{% tab template= "stock-chart/legend", es5Template="es5StockLegendTitle" %}

```typescript

import { StockChart } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
import { DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries } from '@syncfusion/ej2-charts';
import { AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator } from '@syncfusion/ej2-charts';
import { MacdIndicator, RsiIndicator, Trendlines, SmaIndicator, StochasticIndicator, Export, StockLegend } from '@syncfusion/ej2-charts';
import { TmaIndicator, RangeTooltip, Tooltip, Crosshair, ITooltipRenderEventArgs, IStockChartEventArgs, ChartTheme }
from '@syncfusion/ej2-charts';
StockChart.Inject(DateTime, AreaSeries, CandleSeries, HiloOpenCloseSeries, HiloSeries, LineSeries, SplineSeries);
StockChart.Inject(AccumulationDistributionIndicator, AtrIndicator, BollingerBands, EmaIndicator, MomentumIndicator);
StockChart.Inject(MacdIndicator, RsiIndicator, SmaIndicator, StochasticIndicator);
StockChart.Inject(Trendlines, TmaIndicator, RangeTooltip, Tooltip, Crosshair, Export, StockLegend);

let stockChart: StockChart = new StockChart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        indicatorType : [],
        trendlineType : [],
        series: [
            {
                type: 'Candle',
                dataSource: chartData,
                name: 'China'
            }],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {enable: true},
        legendSettings: {
            visible: true,
            title: 'Countries',
            titlePosition: 'Top',
            titleStyle: {
                fontFamily: 'verdana',
                fontStyle: 'Normal',
                fontWeight: 'Normal',
                size: '15px',
                textAlignment: 'Center',
                color: 'blue',
                textOverflow: 'None'
            },
            maximumTitleWidth: 150
        }
});
stockChart.appendTo('#element');
```

{% endtab %}

>Note: To use legend feature, we need to inject `StockLegend` using `StockChart.Inject(StockLegend)`.