---
title: "Funnel | TypeScript "

component: "Accumulation Chart"

description: "The funnel chart displays series value as progressively decreasing amount to hundred percent in total"
---

# Funnel Chart

To render a funnel series, use the series [`type`](../api/accumulation-chart/accumulationSeriesModel/) as `Funnel` and
inject, the `FunnelSeries` module using the `AccumulationChart.Inject(FunnelSeries)` method.

{% tab template= "chart/chart-types", es5Template="es5AccFunnel" %}

```typescript

import { AccumulationChart, FunnelSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(FunnelSeries);

let chart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: [{ x: 'Renewed', y: 18.20, text: 'Renewed 18.20%' }, { x: 'Subscribe', y: 27.3, text: 'Subscribe 27.3%' }, { x: 'Support', y: 55.9, text: 'Support 55.9%' }, { x: 'Downloaded', y: 76.8, text: 'Downloaded 76.8%' },
        { x: 'Visited', y: 100, text: 'Visited 100%' }],
        xName: 'x', yName: 'y',
        }],
}, '#element');

```

{% endtab %}

## Size

The size of the funnel chart can be customized by using the  `width` and `height` properties.

{% tab template= "chart/chart-types", es5Template="es5AccCust" %}

```typescript

import { AccumulationChart, FunnelSeries} from '@syncfusion/ej2-charts';
import { funnelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries);

let chart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: funnelData,
        xName: 'x', yName: 'y',
        //Width of the funnel will be 100% of the chart area
        width: '60%',
        //Height of the funnel will be 100% of the chart area
        height: '80%',
        }],
}, '#element');

```

{% endtab %}

## Neck Size

The funnel's neck size can be customized by using the `neckWidth` and `neckHeight` properties.

{% tab template= "chart/chart-types", es5Template="es5AccNeckSize" %}

```typescript

import { AccumulationChart, FunnelSeries} from '@syncfusion/ej2-charts';
import { funnelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries);

let chart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: funnelData,
        xName: 'x', yName: 'y',

        //Width of the neck will be set as 25% of the chart area
        neckWidth: '25%', neckHeight:'5%',
        }],
}, '#element');

```

{% endtab %}

## Gap Between the Segments

Funnel chart provides options to customize the space between the segments by using the `gapRatio` property of the
series. It ranges from 0 to 1.

{% tab template= "chart/chart-types", es5Template="es5AccGap" %}

```typescript

import { AccumulationChart, FunnelSeries} from '@syncfusion/ej2-charts';
import { funnelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries);

let pyramidchart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: funnelData,
        xName: 'x', yName: 'y',
        // Defines the gap to be left between the segments
        gapRatio: 0.08,
        }],
}, '#element');

```

{% endtab %}

## Explode

Points can be exploded on mouse click by setting the `explode` property to true. You can also explode the point
on load using `explodeIndex`. Explode distance can be set by using `explodeOffset` property.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, FunnelSeries, IAccPointRenderEventArgs } from '@syncfusion/ej2-charts';
import { funnelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries);
let funnelChart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: funnelData,
        xName: 'x', yName: 'y',

        explode: true,

        //Specifies the distance of the point from the center during explode, which takes values in both pixels and percentage
        explodeOffset: '10',

        //If set true, all the points in the series will get exploded on load
        explodeAll: false,

        //Specifies index of the point, to be exploded on load
        explodeIndex:3

        }]
});
funnelChart.appendTo('#element')

```

{% endtab %}

## Smart Data Label

It provides the data label smart arrangement of the funnel and pyramid series. The overlap data label will be placed on left side of the funnel/pyramid series.

{% tab template="chart/chart-types", es5Template="es5AccFunnelDataLabel" %}

```typescript

import {
    AccumulationChart, AccumulationLegend, FunnelSeries, AccumulationTooltip, IAccLoadedEventArgs,
    AccumulationDataLabel, IAccResizeEventArgs, AccumulationTheme
} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationLegend, FunnelSeries, AccumulationTooltip, AccumulationDataLabel);

let data: object[] = [
        { 'x': 'China', y: 1409517397, text: 'China' },
        { 'x': 'India', y: 1339180127, text: 'India' },
        { 'x': 'United States', y: 324459463, text: 'United States' },
        { 'x': 'Indonesia', y: 263991379, text: 'Indonesia' },
        { 'x': 'Brazil', y: 209288278, text: 'Brazil' },
        { 'x': 'Pakistan', y: 197015955, text: 'Pakistan' },
        { 'x': 'Nigeria', y: 190886311, text: 'Nigeria' },
        { 'x': 'Bangladesh', y: 164669751, text: 'Bangladesh' },
        { 'x': 'Russia', y: 143989754, text: 'Russia' },
        { 'x': 'Mexico', y: 129163276, text: 'Mexico' },
        { 'x': 'Japan', y: 127484450, text: ' Japan' },
        { 'x': 'Ethiopia', y: 104957438, text: 'Ethiopia' },
        { 'x': 'Philippines', y: 104918090, text: 'Philippines' },
        { 'x': 'Egypt', y: 97553151, text: 'Egypt' },
        { 'x': 'Vietnam', y: 95540800, text: 'Vietnam' },
        { 'x': 'Germany', y: 82114224, text: 'Germany' }];
    let chart: AccumulationChart = new AccumulationChart({
        //Initializing Chart Series
        series: [{
            type: 'Funnel', dataSource: data, xName: 'x', yName: 'y',
            neckWidth: '15%',
            neckHeight: '18%',
            name: '2017 Population',
            dataLabel: {
                visible: true, position: 'Outside',
                connectorStyle: { length: '6%' }, name: 'text',
            },
            explode: false,
        }],
        legendSettings: {visible: false},
        //Initializing tooltip
        tooltip: { enable: true, format: '${point.x} : <b>${point.y}</b>' },
        load: (args: IAccLoadedEventArgs) => {
            let selectedTheme: string = location.hash.split('/')[1];
            selectedTheme = selectedTheme ? selectedTheme : 'Material';
            args.accumulation.theme = <AccumulationTheme>(selectedTheme.charAt(0).toUpperCase() +
            selectedTheme.slice(1)).replace(/-dark/i, 'Dark');
            if (args.accumulation.availableSize.width < args.accumulation.availableSize.height) {
                args.accumulation.series[0].width = '80%';
                args.accumulation.series[0].height = '70%';
            }
        },
        resized: (args: IAccResizeEventArgs) => {
            let bounds: ClientRect = document.getElementById('container').getBoundingClientRect();
            if (bounds.width < bounds.height) {
                args.accumulation.series[0].width = '80%';
                args.accumulation.series[0].height = '70%';
            } else {
                args.accumulation.series[0].width = '60%';
                args.accumulation.series[0].height = '80%';
            }
        },
        //Initializing Chart title
        title: 'Top population countries in the world 2017',
    });
    chart.appendTo('#element');

```

{% endtab %}

## Customization

Individual points can be customized using the `pointRender` event.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, FunnelSeries, IAccPointRenderEventArgs } from '@syncfusion/ej2-charts';
import { funnelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries);
let funnelChart: AccumulationChart = new AccumulationChart({
    series: [{
        type: 'Funnel',
        dataSource: funnelData,
        xName: 'x', yName: 'y', gapRatio: 0.08}],

    pointRender: (args: IAccPointRenderEventArgs) => {
        if ((args.point.x as string).indexOf('Downloaded') > -1) {
            args.fill = '#f4bc42';
        }
        else {
            args.fill = '#597cf9';
        }
    },
}, '#element');

```

{% endtab %}

## See Also

* [Data label](./data-label/)
* [Grouping](./grouping/)
