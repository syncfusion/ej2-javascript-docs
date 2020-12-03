---
title: " Chart Polar and Radar | TypeScript "

component: "Chart"

description: "Polar and Radar chart supports different draw types and customization to display the data."
---
<!-- markdownlint-disable MD036 -->

# Polar Chart and Radar Chart

## Polar Chart

To render a polar series, use series [`type`](../api/chart/seriesModel/#type-string) as `Polar` and
inject `PolarSeries` module using `Chart.Inject(PolarSeries)` method.

### Draw Types

Polar drawType property is used to change the series plotting type to line, column, area, range column, spline, scatter, stacking area and stacking column. The default value of drawType is `Line`.

**Line**

To render a line draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `Line` and inject `LineSeries` module using `Chart.Inject(LineSeries)` method.

[`isClosed`](../api/chart/seriesModel/#isclosed-boolean) property specifies whether to join start and end point of a line series used in polar chart to form a closed path. Default value of isClosed is true.

{% tab template= "chart/chart-types", es5Template="es5PolarLine" %}

```typescript

import { Chart, LineSeries, PolarSeries } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, PolarSeries);
let chartData: any[] = [
    { x: 2005, y: 28 }, { x: 2006, y: 25 },{ x: 2007, y: 26 }, { x: 2008, y: 27 },
    { x: 2009, y: 32 }, { x: 2010, y: 35 }, { x: 2011, y: 30 }
];
let chart: Chart = new Chart({
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        //Series type as polar
        type: 'Polar',
        // Series draw type as line
        drawType: 'Line'
    }],
}, '#element');

```

{% endtab %}

**Spline**

To render a spline draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `Spline` and
inject `SplineSeries` module using `Chart.Inject(SplineSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5PolarSpline" %}

```typescript

import { Chart, SplineSeries, Category, PolarSeries } from '@syncfusion/ej2-charts';
Chart.Inject(SplineSeries, Category, PolarSeries);
import { polarCategory } from './datasource.ts';


let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: polarCategory,
        xName: 'x', yName: 'y',
        // Series type as Polar series
        type: 'Polar'
        // Series draw type as spline
        drawType: 'Spline'
    }],
}, '#element');

```

{% endtab %}

**Area**

To render a area draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `Area` and inject
`AreaSeries` module using `Chart.Inject(AreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5PolarArea" %}

```typescript

import { Chart, AreaSeries, PolarSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(AreaSeries, PolarSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData,
        xName: 'x', yName: 'y',
        // Series type as polar series
        type: 'Polar'
        // Series draw type as area
        drawType: 'Area'
    }],
}, '#element');

```

{% endtab %}

**Stacked Area**

To render a stacked area draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `StackingArea` and inject `StackingAreaSeries` module
using `Chart.Inject(StackingAreaSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5PolarStackedArea" %}

```typescript

import { Chart, StackingAreaSeries, Category, PolarSeries } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(StackingAreaSeries, Category, PolarSeries);
let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                // Series type as polar series
                type : 'Polar',
                //Series draw type as stacked area series
                drawType: 'StackingArea',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                type : 'Polar',
                drawType: 'StackingArea',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                type : 'Polar',
                drawType: 'StackingArea',
            },
        ],
}, '#element');

```

{% endtab %}

**Column**

To render a column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `Column`.

{% tab template= "chart/chart-types", es5Template="es5PolarColumn" %}

```typescript

import { Chart, Category, PolarSeries, ColumnSeries } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(Category, PolarSeries, ColumnSeries);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        // Series type as polar series
        type: 'Polar',
        // Series draw type as column series
        drawType: 'Column'
    }],
}, '#element');

```

{% endtab %}

**Stacked Column**

To render a stacked column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as
`StackingColumn`.

{% tab template= "chart/chart-types", es5Template="es5PolarStackedColumn" %}

```typescript

import { Chart, Category, PolarSeries, StackingColumnSeries } from '@syncfusion/ej2-charts';
import { stackedData } from './datasource.ts';
Chart.Inject(Category, PolarSeries, StackingColumnSeries);

let chart: Chart = new Chart({
        series: [
            {
                dataSource: stackedData, xName: 'x', yName: 'y',
                type: 'Polar',
                //Series draw type as stacked column
                drawType: 'StackingColumn',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y1',
                type: 'Polar',
                drawType: 'StackingColumn',
            }, {
                dataSource: stackedData, xName: 'x', yName: 'y2',
                type: 'Polar',
                drawType: 'StackingColumn',

            }, {
               dataSource: stackedData, xName: 'x', yName: 'y3',
               type: 'Polar',
               drawType: 'StackingColumn',
            }
        ],
}, '#element');

```

{% endtab %}

**Range Column**

To render a range column draw type, use series [`drawType`](../api/chart/seriesModel/#drawtype-string) as `RangeColumn`.

{% tab template= "chart/chart-types", es5Template="es5PolarRangeColumn" %}

```typescript

import { Chart, Category, PolarSeries, RangeColumnSeries } from '@syncfusion/ej2-charts';
Chart.Inject(Category, PolarSeries, RangeColumnSeries);
let data: any[] = [
    { x: 'Jan', low: 0.7, high: 6.1 }, { x: 'Feb', low: 1.3, high: 6.3 }, { x: 'Mar', low: 1.9, high: 8.5 },
    { x: 'Apr', low: 3.1, high: 10.8 }, { x: 'May', low: 5.7, high: 14.40 }, { x: 'Jun', low: 8.4, high: 16.90 },
    { x: 'Jul', low: 10.6,high: 19.20 }, { x: 'Aug', low: 10.5,high: 18.9 }, { x: 'Sep', low: 8.5, high: 16.1 },
    { x: 'Oct', low: 6.0, high: 12.5 }, { x: 'Nov', low: 1.5, high: 6.9  }, { x: 'Dec', low: 5.1, high: 12.1 }
];

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series: [
        {
            type: 'Polar',
            // Series draw type as range column series
            drawType: 'RangeColumn',
            dataSource: data, xName: 'x', high: 'high', low: 'low',
        }
    ],
    title: 'Maximum and Minimum Temperature'
}, '#element');


```

{% endtab %}

**Scatter**

To render a scatter draw type, use series [`DrawType`](../api/chart/seriesModel/#drawtype-string) as `Scatter` and
inject `ScatterSeries` module using `Chart.Inject(ScatterSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5PolarScatter" %}

```typescript

import { Chart, ScatterSeries, Legend, Category, PolarSeries } from '@syncfusion/ej2-charts';
import { polarCategory } from './datasource.ts';
Chart.Inject(ScatterSeries, Legend, Category, PolarSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: polarCategory,
        xName: 'x', yName: 'y',
        // Series type as Polar series
        type: 'Polar'
        // Series draw type as scatter
        drawType: 'Scatter'
    }],
}, '#element');

```

{% endtab %}

## Radar Chart

To render a radar series, use series [`type`](../api/chart/seriesModel/#type-string) as `Radar` and
inject `PolarSeries` module using `Chart.Inject(RadarSeries)` method.

### Draw Type

similar to Polar drawType, Radar draw property is used to change the series plotting type to line, column, area, range column, spline, scatter, stacking area and stacking column. The default value of drawType is `Line`.

{% tab template= "chart/chart-types", es5Template="es5Radar" %}

```typescript

import { Chart, LineSeries, RadarSeries } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, RadarSeries);

let chart: Chart = new Chart({
    series:[{
        dataSource: numData, xName: 'x', yName: 'y',
        //Series type as polar
        type: 'Radar',
        // Series draw type as line
        drawType: 'Line'
    }],
}, '#element');

```

{% endtab %}

### Customization

**Start Angle**

You can customize the start angle of the polar series using
[`startAngle`](../api/chart/axis/#startangle-number) property. By default, `startAngle` is 0 degree.

{% tab template= "chart/chart-types", es5Template="es5PolarStart" %}

```typescript

import { Chart, Category, PolarSeries } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(Category, PolarSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        // Series type as polar series
        type: 'Polar',
        // Series draw type as column series
        drawType: 'Column'
    }],
}, '#element');

```

{% endtab %}

**Coefficient in axis**

You can customize the radius of the polar series using
[`coefficient`](../api/chart/axis/#coefficient-number) property. By default, `coefficient` is 100.

{% tab template= "chart/chart-types", es5Template="es5PolarCoefficient" %}

```typescript

import { Chart, Category, PolarSeries } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(Category, PolarSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        // Series type as polar series
        type: 'Polar',
        // Series draw type as column series
        drawType: 'Column'
    }],
}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-labels/)
* [Tooltip](./tool-tip/)
