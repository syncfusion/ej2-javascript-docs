---
title: " Chart Types | TypeScript "

component: "Chart"

description: "Essential JS 2 Chart  chart supports 32 types of series and also supports different tpes customizations for each type of chart."
---

# Chart Types

Essential JS 2 Chart  chart supports 32 types of series.

<!-- markdownlint-disable MD036 -->

## Line Chart

<!-- markdownlint-disable MD036 -->

**Line**

To render a line series, use series [`type`](../api/chart/seriesModel/#type-string) as `Line` and
inject `LineSeries` module using `Chart.Inject(LineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5LineDefault" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let chartData: any[] = [
    { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 }, { x: 2008, y: 27 },
    { x: 2009, y: 32 }, { x: 2010, y: 35 }, { x: 2011, y: 30 }
];
let chart: Chart = new Chart({
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        //Series type as line
        type: 'Line'
    }],
}, '#element');

```

{% endtab %}

**Step Line**

To render a step line series, use series [`type`](../api/chart/seriesModel/#type-string) as `StepLine` and
inject `StepLineSeries` module using `Chart.Inject(StepLineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StepLine" %}

```typescript

import { Chart, StepLineSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(StepLineSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        // Series type as StepLine
        type: 'StepLine'
    }],
}, '#element');

```

{% endtab %}

**Stacked Line**

To render a stacked line series, use series [`type`](../api/chart/seriesModel/#type-string) as
`StackingLine` and inject `StackingLineSeries` module
using `Chart.Inject(StackingLineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedLine" %}

```typescript

import { Chart, Category, Legend, Tooltip, StackingLineSeries } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(StackingLineSeries, Category, Legend, Tooltip);

/**
 * Sample for StackedLine Series
 */

let chartData: Object[] = [
    { x: 'Food', y: 90, y1: 40, y2: 70, y3: 120 },
    { x: 'Transport', y: 80, y1: 90, y2: 110, y3: 70 },
    { x: 'Medical', y: 50, y1: 80, y2: 120, y3: 50 },
    { x: 'Clothes', y: 70, y1: 30, y2: 60, y3: 180 },
    { x: 'Personal Care', y: 30, y1: 80, y2: 80, y3: 30 },
    { x: 'Books', y: 10, y1: 40, y2: 30, y3: 270 },
    { x: 'Fitness', y: 100, y1: 30, y2: 70, y3: 40 },
    { x: 'Electricity', y: 55, y1: 95, y2: 55, y3: 75 },
    { x: 'Tax', y: 20, y1: 50, y2: 40, y3: 65 },
    { x: 'Pet Care', y: 40, y1: 20, y2: 80, y3: 95 },
    { x: 'Education', y: 45, y1: 15, y2: 45, y3: 195 },
    { x: 'Entertainment', y: 75, y1: 45, y2: 65, y3: 115 }
];

    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            interval: 1, valueType: 'Category'
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Expense',
            interval: 100,
            labelFormat: '${value}',
        },
        chartArea: { border: { width: 0 } },
        //Initializing Chart Series
        series: [
            {
                type: 'StackingLine', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y', name: 'John'
            },
            {
                type: 'StackingLine', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y1', name: 'Peter'
            },
            {
                type: 'StackingLine', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y2', name: 'Steve'
            },
            {
                type: 'StackingLine', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y3', name: 'Charle'
            }
        ],
        //Initializing User Interaction Tooltip
        tooltip: {
            enable: true
        },
    });

}, '#element');

```

{% endtab %}

**100% Stacked Line**

To render a 100% stacked line series, use series [`type`](../api/chart/seriesModel/#type-string) as
`StackingLine100` and inject `StackingLineSeries`
module using `Chart.Inject(StackingLineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedLine100" %}

```typescript


import { Chart, Category, Legend, Tooltip, StackingLineSeries } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(StackingLineSeries, Category, Legend, Tooltip);

/**
 * Sample for StackedLine Series
 */

let chartData: Object[] = [
    { x: 'Food', y: 90, y1: 40, y2: 70, y3: 120 },
    { x: 'Transport', y: 80, y1: 90, y2: 110, y3: 70 },
    { x: 'Medical', y: 50, y1: 80, y2: 120, y3: 50 },
    { x: 'Clothes', y: 70, y1: 30, y2: 60, y3: 180 },
    { x: 'Personal Care', y: 30, y1: 80, y2: 80, y3: 30 },
    { x: 'Books', y: 10, y1: 40, y2: 30, y3: 270 },
    { x: 'Fitness', y: 100, y1: 30, y2: 70, y3: 40 },
    { x: 'Electricity', y: 55, y1: 95, y2: 55, y3: 75 },
    { x: 'Tax', y: 20, y1: 50, y2: 40, y3: 65 },
    { x: 'Pet Care', y: 40, y1: 20, y2: 80, y3: 95 },
    { x: 'Education', y: 45, y1: 15, y2: 45, y3: 195 },
    { x: 'Entertainment', y: 75, y1: 45, y2: 65, y3: 115 }
];

    let chart: Chart = new Chart({
        primaryXAxis: {
            interval: 1, valueType: 'Category'
        },
        primaryYAxis:
        {
           interval: 20
        },
        chartArea: { border: { width: 0 } },
        series: [
            {
                type: 'StackingLine100', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y', name: 'John'
            },
            {
                type: 'StackingLine100', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y1', name: 'Peter'
            },
            {
                type: 'StackingLine100', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y2', name: 'Steve'

            },
            {
                type: 'StackingLine100', dataSource: chartData, marker: { visible: true },
                dashArray: '5, 1', xName: 'x', width: 2, yName: 'y3', name: 'Charle'

            }
        ],
        tooltip: {
            enable: true,
            format: '${point.x} : <b>${point.y} (${point.percentage}%)</b>'
        },
    });

}, '#element');

```

{% endtab %}

**Spline**

To render a spline series, use series [`type`](../api/chart/seriesModel/#type-string) as `Spline` and
inject `SplineSeries` module using `Chart.Inject(SplineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Spline" %}

```typescript

import { Chart, SplineSeries, Category } from '@syncfusion/ej2-charts';
import { polarCategory } from './datasource.ts';
Chart.Inject(SplineSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: polarCategory,
        xName: 'x', yName: 'y',
        // Series type as spline series
        type: 'Spline'
    }],
}, '#element');

```

{% endtab %}

**Spline Area**

To render a spline area series, use series [`type`](../api/chart/seriesModel/#type-string) as `SplineArea` and
inject `SplineAreaSeries` module using `Chart.Inject(SplineAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Spline" %}

```typescript

import { Chart, SplineAreaSeries, Category } from '@syncfusion/ej2-charts';
import { polarCategory } from './datasource.ts';
Chart.Inject(SplineAreaSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: polarCategory,
        xName: 'x', yName: 'y',
        // Series type as SplineArea
        type: 'SplineArea'
    }],
}, '#element');

```

{% endtab %}

**Multicolored Line**

To render a multicolored line series, use the series type as `MultiColoredLine`, and inject the     `MultiColoredLineSeries` module using `Chart.Inject(MultiColoredLineSeries)` method. Here, the individual colors to the data can be mapped by using `pointColorMapping`.

{% tab template= "chart/chart-types", es5Template="es5LineDefault" %}

```typescript

import { Chart, MultiColoredLineSeries } from '@syncfusion/ej2-charts';
Chart.Inject(MultiColoredLineSeries);
let chart: Chart = new Chart({
    series:[{
        dataSource:  [{ x: 2005, y: 28 , color: 'red'}, { x: 2006, y: 25, color:'green'}, { x: 2007, y: 26, color: '#ff0097' }, { x: 2008, y: 27, color: 'crimson' }, { x: 2009, y: 32, color: 'blue' }, { x: 2010, y: 35 ,color: 'darkorange'}],
        xName: 'x', yName: 'y', pointColorMapping: 'color',
        type: 'MultiColoredLine'
    }],
}, '#element');

```

{% endtab %}

**Customization of Line Chart**

`stroke`, `stroke-width` and `dashArray` of all line type series can be customized by using
[`fill`](../api/chart/seriesModel/#fill-string), [`width`](../api/chart/seriesModel/#width-number) and
[`dashArray`](../api/chart/seriesModel/#dasharray-string) properties.

{% tab template= "chart/chart-types", es5Template="es5LineDashArray" %}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        //fill for chart series
        fill: 'red',
        //line width as 4 for chart series
        width:4,
        //dash array value as 5,5
        dashArray: '5,5',
        xName: 'x', yName: 'y',
        type: 'Line'
    }],
}, '#element');

```

{% endtab %}

## Area Charts

**Area**

To render a [area series](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/area-chart), use series [`type`](../api/chart/seriesModel/#type-string) as `Area` and inject
`AreaSeries` module using `Chart.Inject(AreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Area" %}

```typescript

import { Chart, AreaSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(AreaSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        // Series type as area series
        type: 'Area'
    }],
}, '#element');

```

{% endtab %}

**Range Area**

To render a range area series, use series [`type`](../api/chart/seriesModel/#type-string) as `RangeArea` and inject `RangeAreaSeries` module using `Chart.Inject(RangeAreaSeries)` method.

Since the RangeArea series requires two y values for a point, you have to add the high and low value. High and Low value specifies the maximum and minimum range of the points.

{% tab template= "chart/chart-types", es5Template="es5RangeArea" %}

```typescript

import { Chart, RangeAreaSeries, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(RangeAreaSeries, DateTime);

let series: Object[] = [];
let value: number = 70;
let point: Object;

for (let i: number = 1; i < 70; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point = { x: new Date(1930 + i, 5, i), high: value, low: value - 25 };
    series.push(point);
}

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'DateTime',
    },
    series: [
        {
            type: 'RangeArea',
            dataSource: series,
            xName: 'x', high: 'high', low: 'low',
        }],
}, '#element');

```

{% endtab %}

**Spline Range Area**

The Spline Range Area Chart is used to display continuous data points as a set of splines that vary between high and low values over intervals of time and across different categories.

To render a spline range area series, use series [`type`](../api/chart/seriesModel/#type-string) as `SplineRangeArea` and inject `SplineRangeAreaSeries` module using `Chart.Inject(SplineRangeAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5SplineRangeArea" %}

```typescript

import { Chart, SplineRangeAreaSeries, Category } from '@syncfusion/ej2-charts';
import { splinedata } from './datasource.ts';
Chart.Inject(SplineRangeAreaSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        edgeLabelPlacement: 'Shift',
        majorGridLines: { width: 0 },
    },
    primaryYAxis: {
            labelFormat: '{value}˚C',
            lineStyle: { width: 0 },
            minimum: 0,
            maximum: 40,
            majorTickLines: { width: 0 }
    },
    series: [
        {
            type: 'SplineRangeArea',
            name: 'England',
            dataSource: splinedata,
            xName: 'x', high: 'high', low: 'low',
            opacity: 0.4,
        },
        {
            type: 'SplineRangeArea',
            name: 'India',
            dataSource: splinedata,
            xName: 'x', high: 'high1', low: 'low1',
            opacity: 0.4,
        }],
}, '#element');

```

{% endtab %}

**Stacked Area**

To render a stacked area series, use series [`type`](../api/chart/seriesModel/#type-string) as `StackingArea` and inject `StackingAreaSeries` module
using `Chart.Inject(StackingAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedArea" %}

```typescript

import { Chart, StackingAreaSeries, DateTime } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingAreaSeries, DateTime);

let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                //Series type as stacked area series
                type: 'StackingArea',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                type: 'StackingArea',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                type: 'StackingArea',
            }
        ],

}, '#element');

```

{% endtab %}

**100% Stacked Area**

To render a [100% stacked area](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/100-stacked-area-chart) series, use series [`type`](../api/chart/seriesModel/#type-string) as `StackingArea100`
and inject `StackingAreaSeries` module using `Chart.Inject(StackingAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedArea100" %}

```typescript

import { Chart, StackingAreaSeries, DateTime } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingAreaSeries, DateTime);

let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                //Series type as 100% stacked area series
                type: 'StackingArea100',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                type: 'StackingArea100',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                type: 'StackingArea100',
            }
        ],

}, '#element');

```

{% endtab %}

**Step Area**

To render a step area series, use series [`type`](../api/chart/seriesModel/#type-string) as `StepArea`
and inject `StepAreaSeries` module using `Chart.Inject(StepAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StepArea" %}

```typescript

import { Chart, StepAreaSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(StepAreaSeries);

let chart: Chart = new Chart({
   series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        type: 'StepArea'
    }],

}, '#element');

```

{% endtab %}

**Stacked Step Area**

To render a stacked step area series, use series `type` as `StackingStepArea`
and inject `StackingStepAreaSeries` module using `Chart.Inject(StackingStepAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedStepArea" %}

```typescript

import { Chart, StackingStepAreaSeries } from '@syncfusion/ej2-charts';
Chart.Inject(StackingStepAreaSeries);

let chart: Chart = new Chart({
   series:[
       {
        dataSource: [{ x: 2000, y: 416 }, { x: 2001, y: 490 }, { x: 2002, y: 470 }, { x: 2003, y: 500 },
                { x: 2004, y: 449 }, { x: 2005, y: 470 }, { x: 2006, y: 437 }, { x: 2007, y: 458 },
                { x: 2008, y: 500 }, { x: 2009, y: 473 }, { x: 2010, y: 520 }, { x: 2011, y: 509 }],
        xName: 'x', yName: 'y',
        type: 'StackingStepArea'
       },
       {
        dataSource: [{ x: 2000, y: 180 }, { x: 2001, y: 240 }, { x: 2002, y: 370 }, { x: 2003, y: 200 },
                { x: 2004, y: 229 }, { x: 2005, y: 210 }, { x: 2006, y: 337 }, { x: 2007, y: 258 },
                { x: 2008, y: 300 }, { x: 2009, y: 173 }, { x: 2010, y: 220 }, { x: 2011, y: 309 }],
        xName: 'x', yName: 'y',
        type: 'StackingStepArea'
       }
    ],

}, '#element');

```

{% endtab %}

**Multicolored area**

To render a multicolored area series, use the series type as `MultiColoredArea`, and inject the `MultiColoredAreaSeries` module using `Chart.Inject(MultiColoredAreaSeries)` method. The required `segments` of the series can be customized using the `value`, `color`, and `dashArray`.

{% tab template= "chart/chart-types", es5Template="es5StepArea" %}

```typescript

import { Chart, MultiColoredAreaSeries } from '@syncfusion/ej2-charts';
Chart.Inject(MultiColoredAreaSeries);

let chart: Chart = new Chart({
   series:[{
        dataSource:  [{ x: 2005, y: 28 }, { x: 2006, y: 25}, { x: 2007, y: 26 }, { x: 2008, y: 27 },
        { x: 2009, y: 32}, { x: 2010, y: 35 }, { x: 2011, y: 25 }],
        xName: 'x', yName: 'y',
        type: 'MultiColoredArea',
        segmentAxis: 'X',
        segments: [{
                    value: 2007,
                    color: 'blue'
                }, {
                    value: 2009,
                    color: 'lightgreen'
                }, {
                    color: 'orange'
        }],
    }],

}, '#element');

```

{% endtab %}

**Customization of Area Series**

`fill`, `border` and `dashArray` of all area type series can be customized
using [`fill`](../api/chart/seriesModel/#fill-string),
[`border`](../api/chart/series/#border-bordermodel)
and [`dashArray`](../api/chart/seriesModel/#dasharray-string) properties.

{% tab template= "chart/chart-types", es5Template="es5AreaCus" %}

```typescript

import { Chart, AreaSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(AreaSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        fill:'#69D2E7',
        border:{width:2, color:'Red'},
        dashArray: '5,5',
        name: 'Product A',
        type: 'Area'
    }],

}, '#element');

```

{% endtab %}

## Column Chart

**Column**

To render a [column series](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/column-chart), use series [`type`](../api/chart/seriesModel/#type-string) as `Column` and
inject `ColumnSeries` module using `Chart.Inject(ColumnSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Column" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        // Series type as column series
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

**Stacked Column**

To render a stacked column series, use series [`type`](../api/chart/seriesModel/#type-string) as
`StackingColumn` and inject `StackingColumnSeries` module
using `Chart.Inject(StackingColumnSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedColumn" %}

```typescript

import { Chart, StackingColumnSeries, Category } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingColumnSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                //Series type as stacked column
                type: 'StackingColumn'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                 type: 'StackingColumn'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                 type: 'StackingColumn'

            }
        ],

}, '#element');

```

{% endtab %}

**100% Stacked Column**

To render a [100% stacked column](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/100-stacked-column-chart) series, use series [`type`](../api/chart/seriesModel/#type-string) as
`StackingColumn100` and inject `StackingColumnSeries`
module using `Chart.Inject(StackingColumnSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedColumn100" %}

```typescript

import { Chart, StackingColumnSeries, DateTime } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingColumnSeries, DateTime);

let chart: Chart = new Chart({
       series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                //Series type as 100% stacked column series
                type: 'StackingColumn100'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                 type: 'StackingColumn100'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                 type: 'StackingColumn100'
            }
        ],

}, '#element');

```

{% endtab %}

**Range Column**

To render a range column series, use series [`type`](../api/chart/seriesModel/#type-string) as `RangeColumn`
and inject `RangeColumnSeries` module
using `Chart.Inject(RangeColumnSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5RangeColumn" %}

```typescript

import { Chart, RangeColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(RangeColumnSeries, Category);
let data: any[] = [
    { x: 'Jan', low: 0.7, high: 6.1 }, { x: 'Feb', low: 1.3, high: 6.3 }, { x: 'Mar', low: 1.9, high: 8.5 },
    { x: 'Apr', low: 3.1, high: 10.8 }, { x: 'May', low: 5.7, high: 14.40 }, { x: 'Jun', low: 8.4, high: 16.90 },
    { x: 'Jul', low: 10.6,high: 19.20 }, { x: 'Aug', low: 10.5,high: 18.9 }, { x: 'Sep', low: 8.5, high: 16.1 },
    { x: 'Oct', low: 6.0, high: 12.5 }, { x: 'Nov', low: 1.5, high: 6.9  }, { x: 'Dec', low: 5.1, high: 12.1 }
];
let data2: any[] = [
    { x: 'Jan', low: 1.7, high: 7.1 }, { x: 'Feb', low: 1.9, high: 7.7 }, { x: 'Mar', low: 1.2, high: 7.5 },
    { x: 'Apr', low: 2.5, high: 9.8 }, { x: 'May', low: 4.7, high: 11.4 }, { x: 'Jun', low: 6.4, high: 14.4 },
    { x: 'Jul', low: 9.6, high: 17.2 }, { x: 'Aug', low: 10.7, high: 17.9 }, { x: 'Sep', low: 7.5, high: 15.1 },
    { x: 'Oct', low: 3.0, high: 10.5 }, { x: 'Nov', low: 1.2, high: 7.9 }, { x: 'Dec', low: 4.1, high: 9.1 }
];

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series: [
        {
            // Series type as range column series
            type: 'RangeColumn',
            dataSource: data, xName: 'x', high: 'high', low: 'low',
        }, {
            type: 'RangeColumn',
            dataSource: data2, xName: 'x', high: 'high', low: 'low',
        }
    ],

}, '#element');


```

{% endtab %}

**Customization of Column**

`fill`, `border` and `dashArray` of all column type series can be
customized using [`fill`](../api/chart/seriesModel/#fill-string) , [`border`](../api/chart/borderModel/)  and [`dashArray`](../api/chart/seriesModel/#dasharray-string) properties.

{% tab template= "chart/chart-types", es5Template="es5ColumnCust" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        //fill for column series
        fill: 'green',
        //border width and color for column series
        border: {
            width: '2',
            color: 'red'
        },
        //dash array for the series
        dashArray: '5,3',
        //series type as column series
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

**Stacking Group**

You can use the [`stackingGroup`](../api/chart/series/#stackinggroup-string) property to group the stacked columns and 100% stacked columns.
Columns with same group name are stacked on top of each other.

{% tab template= "chart/chart-types", es5Template="es5StackingColumnGroup" %}

```typescript

import { Chart, StackingColumnSeries, Category } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingColumnSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                type: 'StackingColumn'
                //Stacking group for stacked column series
                stackingGroup: 'UKAndGermany'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                type: 'StackingColumn', stackingGroup: 'UKAndGermany'
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                type: 'StackingColumn', stackingGroup: 'FranceAndItaly'

            }
        ],

}, '#element');

```

{% endtab %}

## Bar Chart

**Bar**

To render a [bar series](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/bar-chart), use series [`type`](../api/chart/seriesModel/#type-string) as `Bar` and inject
`BarSeries` module using `Chart.Inject(BarSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Bar" %}

```typescript

import { Chart, BarSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(BarSeries, Category);

let chart: Chart = new Chart({
   series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        // Series type as bar series
        type: 'Bar'
    }],

}, '#element');

```

{% endtab %}

**Stacked bar**

To render a stacked bar series, use series [`type`](../api/chart/seriesModel/#type-string) as `StackingBar`
and inject `StackingBarSeries` module
using `Chart.Inject(StackingBarSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedBar" %}

```typescript

import { Chart, StackingBarSeries, Category } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingBarSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                //Series type as stacked bar
                type: 'StackingBar',
                dataSource: stackedData, xName: 'x', yName: 'y'
            }, {
                type: 'StackingBar',
                dataSource: stackedData, xName: 'x', yName: 'y1'
            }, {
               type: 'StackingBar',
                dataSource: stackedData, xName: 'x', yName: 'y2'
            }
        ],

}, '#element');

```

{% endtab %}

**100% Stacked Bar**

To render a [100% stacked bar](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/100-stacked-bar-chart) series, use series [`type`](../api/chart/seriesModel/#type-string) as
`StackingBar100` and inject `StackingBarSeries`
module using `Chart.Inject(StackingBarSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5StackedBar100" %}

```typescript

import { Chart, StackingBarSeries, Category } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingBarSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                //Series type as 100% stacked bar
                type: 'StackingBar100',
                dataSource: stackedData, xName: 'x', yName: 'y'
            }, {
                type: 'StackingBar100',
                dataSource: stackedData, xName: 'x', yName: 'y1'
            }, {
               type: 'StackingBar100',
                dataSource: stackedData, xName: 'x', yName: 'y2'
            }
        ],

}, '#element');

```

{% endtab %}

**Customization of Bar Series**

`fill`, `border` and `dashArray` of all bar type series can be
customized using [`fill`](../api/chart/seriesModel/#fill-string), [`border`](../api/chart/borderModel/) and [`dashArray`](../api/chart/seriesModel/#dasharray-string) properties.

{% tab template= "chart/chart-types", es5Template="es5BarCust" %}

```typescript

import { Chart, BarSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(BarSeries, Category);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        //fill for bar series
        fill: 'green',
        //border for bar series
        border: {
            width: 2,
            color: 'red'
        },
        //dashArray for bar series
        dashArray: '5,3',
        // series type as bar series
        type: 'Bar'
    }],

}, '#element');

```

{% endtab %}

**Stacking Group**

You can use the [`stackingGroup`](../api/chart/series/#stackinggroup-string) property to group the stacked bar and 100% stacked bar.
Columns with same group name are stacked on top of each other.

{% tab template= "chart/chart-types", es5Template="es5StackingBarGroup" %}

```typescript

import { Chart, StackingBarSeries } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingBarSeries);

let chart: Chart = new Chart({
       series: [
            {
                type: 'StackingBar',
                //Stacking group for stacked bar
                stackingGroup: 'JohnAndAndrew',
                dataSource: stackedData, xName: 'x', yName: 'y'
            }, {
                type: 'StackingBar', name: 'Andrew', stackingGroup: 'JohnAndAndrew',
                dataSource: stackedData, xName: 'x', yName: 'y1'
            }, {
               type: 'StackingBar', name: 'Thomas', stackingGroup: 'ThomasAndMichael',
               dataSource: stackedData, xName: 'x', yName: 'y2'
            }
        ],

}, '#element');

```

{% endtab %}

## Scatter Charts

To render a scatter series, use series [`type`](../api/chart/seriesModel/#type-string) as `Scatter` and
inject `ScatterSeries` module using `Chart.Inject(ScatterSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Scatter" %}

```typescript

import { Chart, ScatterSeries, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ScatterSeries, Legend);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 50; i++) {
    if (Math.random() > 0.5) {
        value1 += Math.random();
    } else {
        value1 -= Math.random();
    }
    value1 = value1 < 60 ? 60 : value1 > 90 ? 90 : value1;
    point1 = { x: 120 + (i / 2), y: value1.toFixed(1) };
    series2.push(point1);
}

let chart: Chart = new Chart({
   series: [
        {
            //Series type as scatter
            type: 'Scatter',
            dataSource: series1, xName: 'x', yName: 'y',

        }, {
            type: 'Scatter',
            dataSource: series2, xName: 'x', yName: 'y',
        }
    ],

}, '#element');

```

{% endtab %}

## Bubble Chart

To render a [bubble series](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/bubble-charts), use series [`type`](../api/chart/seriesModel/#type-string) as `Bubble` and
inject `BubbleSeries` module using `Chart.Inject(BubbleSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5Bubble" %}

```typescript

import { Chart, BubbleSeries} from '@syncfusion/ej2-charts';
import { EmitType } from '@syncfusion/ej2-base';
Chart.Inject(BubbleSeries);
    let chart: Chart = new Chart({
        series: [
            {
                type: 'Bubble',
                dataSource: [{ x: 92.2, y: 7.8, size: 1.347, text: 'China' },
                { x: 74, y: 6.5, size: 1.241, text: 'India' },
                { x: 90.4, y: 6.0, size: 0.238, text: 'Indonesia' },
                { x: 99.4, y: 2.2, size: 0.312, text: 'US' },
                { x: 88.6, y: 1.3, size: 0.197, text: 'Brazil' },
                { x: 99, y: 0.7, size: 0.0818, text: 'Germany' },
                { x: 72, y: 2.0, size: 0.0826, text: 'Egypt' },
                { x: 99.6, y: 3.4, size: 0.143, text: 'Russia' },
                { x: 99, y: 0.2, size: 0.128, text: 'Japan' },
                { x: 86.1, y: 4.0, size: 0.115, text: 'Mexico' },
                { x: 92.6, y: 6.6, size: 0.096, text: 'Philippines' },
                { x: 61.3, y: 14.5, size: 0.162, text: 'Nigeria' }],
                xName: 'x', yName: 'y', size: 'size',
            },
        ],

}, '#element');

```

{% endtab %}

 **Bubble Size Mapping**

`size` property can be used to map the size value specified in data source.

{% tab template= "chart/chart-types", es5Template="es5Bubble" %}

```typescript

import { Chart, BubbleSeries} from '@syncfusion/ej2-charts';
import { bubbleData } from './datasource.ts';
import { EmitType } from '@syncfusion/ej2-base';
Chart.Inject(BubbleSeries);
    let chart: Chart = new Chart({
        series: [
            {
                type: 'Bubble',
                dataSource: bubbleData,
                xName: 'x', yName: 'y',
                //size property used to map size values from data source
                size: 'size',
            },
        ],

}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)