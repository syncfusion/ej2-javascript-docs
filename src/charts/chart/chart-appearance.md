---
title: " Chart Appearance | TypeScript "

component: "Chart"

description: "We can customize chart appearance by using color palette, point level customization, chart area cutomization, title and margin customizations."
---

# Appearance

## Custom Color Palette

You can customize the default color of series or points by providing a custom color palette of your choice by
using the [`palettes`](../api/chart/#palettes-string) property.

{% tab template= "chart/chart-appearance", es5Template="es5Pallete" %}

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
    // palettes for chart
    palettes: ["#E94649", "#F6B53F", "#6FAAB0", "#C4C24A"],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Point Level Customization

Marker, data label and fill color of each data point can be customized with
[`pointRender`](../api/chart/#pointrender-emittypeipointrendereventargs) and
[`textRender`](../api/chart/#textrender-emittypeitextrendereventargs) event.

{% tab template= "chart/chart-appearance", es5Template="es5PointCust" %}

```typescript

import { Chart, ColumnSeries, Category, ISeriesRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
];
let colors: string[] = ['#00bdae', '#404041', '#357cd2', '#e56590', '#f8b883',
                '#70ad47', '#dd8abd', '#7f84e8', '#7bb4eb', '#ea7a57'];
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
    }],
    // point render event for chart
    pointRender: (args: IPointRenderEventArgs): void => {
        args.fill = colors[args.point.index];
    },
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Chart Area Customization

<!-- markdownlint-disable MD036 -->

**Customize the Chart Background**

Using [`background`](../api/chart/#background-string) and
[`border`](../api/chart/#border-bordermodel) properties, you can change the background color and border
of the chart.

{% tab template= "chart/chart-appearance", es5Template="es5ChartBackRound" %}

```typescript

import { Chart, ColumnSeries, Category, ISeriesRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
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
        name: 'Gold', type: 'Column',
        border:{ width: 2, color: 'grey'}
    }]
    title: 'Olympic Medals',
    //Customizing Chart background
    background: 'skyblue',
    //Customize the chart border and opacity
    border: {color: "#FF0000", width: 2},
}, '#element');

```

{% endtab %}

**Chart Margin**

You can set margin for chart from its container through [`margin`](../api/chart/#margin-marginmodel) property.

{% tab template= "chart/chart-appearance", es5Template="es5ChartMargin" %}

```typescript

import { Chart, ColumnSeries, Category, ISeriesRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
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
        name: 'Gold', type: 'Column',
        border:{ width: 2, color: 'grey'}
    }]
    title: 'Olympic Medals',
    background: 'skyblue',
    border: {color: "#FF0000", width: 2},
    //Change chart margin to left, right, top and bottom
    margin: { left: 40, right: 40, top: 40, bottom: 40 },
}, '#element');

```

{% endtab %}

**Chart Area Background**

The chart area background can be customized by using the [`background`](../api/chart/#background-string)
property in the [`chartArea`](../api/chart/#chartarea-chartareamodel).

{% tab template= "chart/chart-appearance", es5Template="es5AreaBack" %}

```typescript

import { Chart, ColumnSeries, Category, ISeriesRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
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
        name: 'Gold', type: 'Column',
        border:{ width: 2, color: 'grey'}
    }]
    title: 'Olympic Medals',
    chartArea: {
        //background for Chart area
        background: "skyblue"
    }
}, '#element');

```

{% endtab %}

## Animation

You can customize animation for a particular series using [`animation`](../api/chart//animationModel/) property.
You can enable or disable animation of the series using `enable` property, `duration` specifies the duration
of an animation and `delay` allows us to start the animation at desire time.

{% tab template= "chart/chart-appearance", es5Template="es5Animation" %}

```typescript

import { Chart, ColumnSeries, Category, ISeriesRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
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
        name: 'Gold', type: 'Column',
        border:{ width: 2, color: 'grey'},
        //Animation for chart series
        animation:{
            enable: true,
            duration: 2000,
            delay: 200
        }
    }],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

### Fluid Animation

Fluid animation used to animate series with updated dataSource continues animation rather than animation whole series. You can customize animation for a particular series using [`animate`] method.

{% tab template= "chart/chart-appearance", es5Template="es5FluidAnimation" %}

```typescript

import {
    Chart, ColumnSeries, Category, DataLabel,Tooltip, ILoadedEventArgs
} from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Category, Tooltip);
    let count: number = 0;
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category', interval: 1, majorGridLines: { width: 0 },
            tickPosition: 'Inside',
            labelPosition: 'Inside', labelStyle: { color: '#ffffff' }
        },
        chartArea: { border: { width: 0 } },
        //Initializing Primary Y Axis
        primaryYAxis:
            {
                minimum: 0, maximum: 300, interval: 50, majorGridLines: { width: 0 },
                majorTickLines: { width: 0 }, lineStyle: { width: 0 }, labelStyle: { color: 'transparent' }
            },

        //Initializing Chart Series
        series: [
            {
                type: 'Column', xName: 'x', width: 2, yName: 'y',
                dataSource: [
                    { x: 'Egg', y: 106 },
                    { x: 'Fish', y: 103 },
                    { x: 'Misc', y: 198 },
                    { x: 'Tea', y: 189 },
                    { x: 'Fruit', y: 250 }
                ], name: 'Tiger',
                cornerRadius: {
                    bottomLeft: 10, bottomRight: 10, topLeft: 10, topRight: 10
                },
            }
        ],
        legendSettings: { visible: false },
        //Initializing Chart title
        title: 'Trade in Food Groups', tooltip: { enable: false },
        loaded: (args: ILoadedEventArgs) => {
            let columninterval = setInterval(
                () => {
                    if (document.getElementById('element')) {
                        if (count === 0) {
                            chart.series[0].dataSource = [
                                { x: 'Egg', y: 206 },
                                { x: 'Fish', y: 123 },
                                { x: 'Misc', y: 48 },
                                { x: 'Tea', y: 240 },
                                { x: 'Fruit', y: 170 }
                            ];
                            chart.animate();
                            count++;
                        }
                        else if (count === 1) {
                            chart.series[0].dataSource = [
                                { x: 'Egg', y: 86 },
                                { x: 'Fish', y: 173 },
                                { x: 'Misc', y: 188 },
                                { x: 'Tea', y: 109 },
                                { x: 'Fruit', y: 100 }
                            ];
                            chart.animate();
                            count++;
                        }
                        else if (count === 2) {
                            chart.series[0].dataSource = [
                                { x: 'Egg', y: 156 },
                                { x: 'Fish', y: 33 },
                                { x: 'Misc', y: 260 },
                                { x: 'Tea', y: 200 },
                                { x: 'Fruit', y: 30 }
                            ];
                            chart.animate();
                            count = 0;
                        }
                    } else {
                        clearInterval(columninterval);
                    }
                },
                2000
            );
        },
}, '#element');

```

{% endtab %}

## Chart Title

Chart can be given a title using [`title`](../api/chart/#title-string) property, to show the information
about the data plotted.

{% tab template= "chart/chart-appearance", es5Template="es5Title" %}

```typescript

import { Chart, StepLineSeries, DateTime, Legend, Tooltip } from '@syncfusion/ej2-charts';
Chart.Inject(StepLineSeries, DateTime, Legend, Tooltip);

let chartData: any[] = [
    { x: new Date(1975, 0, 1), y: 16, y1: 10, y2: 4.5 },
    { x: new Date(1980, 0, 1), y: 12.5, y1: 7.5, y2: 5 },
    { x: new Date(1985, 0, 1), y: 19, y1: 11, y2: 6.5 },
    { x: new Date(1990, 0, 1), y: 14.4, y1: 7, y2: 4.4 },
    { x: new Date(1995, 0, 1), y: 11.5, y1: 8, y2: 5 },
    { x: new Date(2000, 0, 1), y: 14, y1: 6, y2: 1.5 },
    { x: new Date(2005, 0, 1), y: 10, y1: 3.5, y2: 2.5 },
    { x: new Date(2010, 0, 1), y: 16, y1: 7, y2: 3.7 }
];
let chart: Chart = new Chart({

        primaryXAxis: {
            title: 'Years',
            lineStyle: { width: 0 },
            labelFormat: 'y',
            intervalType: 'Years',
            valueType: 'DateTime',
            edgeLabelPlacement: 'Shift'
        },

        primaryYAxis:
        {
            title: 'Percentage (%)',
            minimum: 0, maximum: 20, interval: 2,
            labelFormat: '{value}%'
        },
        series: [
            {
                type: 'StepLine',
                dataSource: chartData, xName: 'x', yName: 'y',
                width: 2, name: 'China',
                marker: {
                    visible: true, width: 10, height: 10
                },
            },
            {
                type: 'StepLine',
                dataSource: chartData, xName: 'x', yName: 'y1',
                width: 2, name: 'Australia',
                marker: {
                    visible: true, width: 10, height: 10
                },
            },
            {
                type: 'StepLine',
                dataSource: chartData, xName: 'x', yName: 'y2',
                width: 2, name: 'Japan',
                marker: {
                    visible: true, width: 10, height: 10
                },

            },
        ],
        //Title for chart
        title: 'Unemployment Rates 1975-2010',
        titleStyle:{
            fontFamily: "Arial",
            fontStyle: 'italic',
            fontWeight: 'regular',
            color: "#E27F2D",
            size: '23px'
        }
}, '#element');

```

{% endtab %}

**Title wrap**

The `textStyle` property of chart title provides options to customize the `size`, `color`, `fontFamily`, `fontWeight`, `fontStyle`, `opacity`, `textAlignment` and `textOverflow`.

{% tab template= "chart/getting-started", es5Template="es5chartTitle"%}

```typescript

import { Chart, LineSeries } from '@syncfusion/ej2-charts';
import { Legend, Category, Tooltip } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Legend, Category, Tooltip);
let chartData: any[] = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    title: 'Sales Analysis',
    textStyle:{size:'18px', color:'Red', textAlignment: 'Far', textOverflow: 'Wrap' },
    series:[{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Line'
    }],
}, '#element');

```

{% endtab %}

## See Also

* [Customize the series points using patterns](../chart/how-to/points-customization/#customize-the-series-points-by-using-patterns)
