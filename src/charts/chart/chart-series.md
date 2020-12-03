---
title: " Chart Series | TypeScript "

component: "Chart"

description: "Chart supports to render collection of series like multiple series or combination series."
---

# Chart Series

## Multiple Series

You can add multiple series to the chart by using [`series`](../api/chart/seriesModel/) property.
The series are rendered in the order as it is added to the series array.

{% tab template= "chart/chart-series", es5Template="es5MultipleSeries" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Combination Series

Chart allows you to render [combination of different series](https://www.syncfusion.com/javascript-ui-controls/js-charts/chart-types/combination-chart) like Column, line, area etc.

>Bar series cannot be combined with any other series as the axis orientation is different from other series.

{% tab template= "chart/chart-series", es5Template="es5CombinationSeries" %}

```typescript

import { Chart, StackingColumnSeries, LineSeries } from '@syncfusion/ej2-charts';
import { ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(StackingColumnSeries, LineSeries, Category, ColumnSeries);
let chartData: any[] = [
    { x: '2005', y: 1.2, y1: 0.5, y2: 0.7, y3: -0.8, y4: 1.5 },
    { x: '2006', y: 1, y1: 0.5, y2: 1.4, y3: 0, y4: 2.3 },
    { x: '2007', y: 1, y1: 0.5, y2: 1.5, y3: -1, y4: 2 },
    { x: '2008', y: 0.25, y1: 0.35, y2: 0.35, y3: -.35, y4: 0.1 },
    { x: '2009', y: 0.1, y1: 0.9, y2: -2.7, y3: -0.3, y4: -2.7 },
    { x: '2010', y: 1, y1: 0.5, y2: 0.5, y3: -0.5, y4: 1.8 },
    { x: '2011', y: 0.1, y1: 0.25, y2: 0.25, y3: 0, y4: 2 },
    { x: '2012', y: -0.25, y1: -0.5, y2: -0.1, y3: -0.4, y4: 0.4 },
    { x: '2013', y: 0.25, y1: 0.5, y2: -0.3, y3: 0, y4: 0.9 },
    { x: '2014', y: 0.6, y1: 0.6, y2: -0.6, y3: -0.6, y4: 0.4 },
    { x: '2015', y: 0.9, y1: 0.5, y2: 0, y3: -0.3, y4: 1.3 }
];
let chart: Chart = new Chart({
        primaryXAxis: {
            title: 'Years',
            interval: 1,
            labelIntersectAction : 'Rotate45',
            valueType: 'Category'
        },
        primaryYAxis:
        {
            title: 'Growth',
            minimum: -3, maximum: 3, interval: 1
        },
        series: [
            {
                type: 'StackingColumn', dataSource: chartData,
                xName: 'x', yName: 'y', name: 'Private Consumption'
            }, {
                type: 'StackingColumn', dataSource: chartData,
                xName: 'x', yName: 'y1', name: 'Government Consumption'
            }, {
                type: 'StackingColumn', dataSource: chartData,
                xName: 'x', yName: 'y2', name: 'Investment'
            }, {
                type: 'StackingColumn', dataSource: chartData,
                xName: 'x', yName: 'y3', name: 'Net Foreign Trade'

            }, {
                type: 'Line',  name: 'GDP',
                dataSource: chartData, xName: 'x', yName: 'y4',
                width: 2, opacity: 0.6,
                marker: {
                    visible: true,
                    width: 10, opacity: 0.6,
                    height: 10
                },
            }
        ],
        title: 'Annual Growth GDP in France'
}, '#element');

```

{% endtab %}

## Enable Complex Property in Series

By setting `enableComplexProperty` value as `true` in series you can bind complex data to the chart.

{% tab template= "chart/chart-series", es5Template="es5CombinationSeries" %}

```typescript

import { Chart, LineSeries, DateTime, Legend, Tooltip, ILoadedEventArgs, ChartTheme,Category, ColumnSeries, } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(LineSeries, DateTime,Category, ColumnSeries, Legend, Tooltip);

/**
 * Sample for Line series
 */
export let data: any[] = [
  {group: { x: 'Aaa', y: 10}, y: 20},
  {group: { x: 'Baa', y: 30}, y: 10}
];
    let chart: Chart = new Chart({

        //Initializing Primary X Axis
        primaryXAxis: {
                valueType: 'Category'
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Column',
                dataSource: data,
                enableComplexProperty: true,
                xName: 'group.x', yName: 'group.y',
            },
             {
                type: 'Column',
                dataSource: data,
                enableComplexProperty: true,
                xName: 'group.x', yName: 'y',
            },
        ]
    }, '#element');

```

{% endtab %}