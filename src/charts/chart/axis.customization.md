---
title: " Chart Axis Customization | TypeScript "

component: "Chart"

description: "Chart axis contains different customization and types like axis crossing, multiple axis, inversed axis, tick and grid, title customizations"
---

# Axis Customization

## Axis Crossing

An axis can be positioned in the chart area using `crossesAt` and `crossesInAxis` properties. The `crossesAt` property specifies the values (datetime, numeric, or logarithmic) at which the axis line has to be intersected with the vertical axis or vice-versa, and the `crossesInAxis` property specifies the axis name with which the axis line has to be crossed.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { stripData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        crossesAt : 15
    },
    primaryXAxis: {
        crossesAt : 5
    },
    series:[{
        dataSource: stripData,
        xName: 'x', yName: 'y',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Title

You can add a title to the axis using [`title`](../api/chart/axis/) property to provide quick
information to the user about the data plotted in the axis. Title style can be customized using `titleStyle` property of the axis.

{% tab template= "chart/axis", es5Template="es5AxisTitle" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries',
        //Axis title text style
        titleStyle: {
            size: '16px', color: 'grey',
            fontFamily : 'Segoe UI', fontWeight : 'bold'
        }
    },
   series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Tick Lines Customization

You can customize the  `width`, `color` and `size` of the minor and major tick lines, using
[`majorTickLines`](../api/chart/axis/) and
[`minorTickLines`](../api/chart/axis/) properties in the axis.

{% tab template= "chart/axis", es5Template="es5TickLines" %}

```typescript

import { Chart, Category, ColumnSeries } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
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
            color : 'blue',
            width : 5
        },
        minorTickLines : {
            color : 'red',
            width : 0
        }
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Grid Lines Customization

You can customize the `width`, `color` and `dashArray` of the minor and major grid lines, using [`majorGridLines`](../api/chart/axis/)
and [`minorGridLines`](../api/chart/axis/) properties in the axis.

{% tab template= "chart/axis", es5Template="es5GridLines" %}

```typescript

import { Chart, Category, ColumnSeries } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
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
            color : 'blue',
            width : 1
        },
        minorGridLines : {
            color : 'red',
            width : 0
        }
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Multiple Axis

In addition to primary X and Y axis, we can add n number of axis to the chart. Series can be associated with
this axis, by mapping with axis's unique name.

{% tab template= "chart/axis", es5Template="es5MultipleAxis" %}

```typescript

import { Chart, Category, ColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, LineSeries);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    // Initializing multiple axis
    axes:[
        {
            rowIndex: 0,
            name: 'yAxis',
        }
    ],
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    },{
        dataSource: categoryData,
        xName: 'country', yName: 'silver',
        yAxisName: 'yAxis',
        type: 'Line',
    }],

}, '#element');

```

{% endtab %}

## Inversed Axis

<!-- markdownlint-disable MD033 -->

When an axis is inversed, highest value of the axis comes closer to origin and vice versa. To place an axis in inversed manner set this property
 [`isInversed`](../api/chart/axis/) to true.

{% tab template= "chart/axis", es5Template="es5InversedAxis" %}

```typescript

import { Chart, LineSeries, Category, Legend, DataLabel } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(LineSeries, Category, Legend, DataLabel);
/**
 * inversed axis sample
 */
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
             isInversed: true
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
             isInversed: true
        },
        series: [
            {
                type: 'Line',
                dataSource: categoryData,
                xName: 'country',
                yName: 'gold',
            },
        ],
        title: 'Exchange rate',
    }, '#element');

```

{% endtab %}

## Opposed Position

To place an axis opposite from its original position,
set [`opposedPosition`](../api/chart/axis/) property of the axis to true.

{% tab template= "chart/axis", es5Template="es5InversedAxis" %}

```typescript

import { Chart, LineSeries, Category, Legend, DataLabel } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(LineSeries, Category, Legend, DataLabel);
/**
 * inversed axis sample
 */
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
        },

        //Initializing Primary Y Axis
        primaryYAxis:
        {
             //Axis position as opposite
        opposedPosition: true
        },
        series: [
            {
                type: 'Line',
                dataSource: categoryData,
                xName: 'country',
                yName: 'gold',
            },
        ],
        title: 'Exchange rate',
    }, '#element');

```

{% endtab %}