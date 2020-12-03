---
title: " Chart Crosshair and Trackball | TypeScript "

component: "Chart"

description: "Crosshair has a vertical and horizontal line to view the value of the axis at mouse position.The trackball used to display data collections"
---

# Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairTooltip/#enable-boolean) property in the `crosshair`. Likewise tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel/#enable-boolean) property of `crosshairTooltip` in the corresponding axis.

{% tab template= "chart/user-interaction", es5Template="es5CrossHair" %}

```typescript

import { Chart, LineSeries, Crosshair, DateTime, Legend } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Crosshair, Legend);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Line', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            }
        ],
        //crosshair for chart
        crosshair: { enable: true },
        legendSettings: { visible: true },
        title: 'Weather Condition'
}, '#element');

```

{% endtab %}

## Tooltip for axis

Tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel/#enable-boolean) property of `crosshairTooltip` in the corresponding axis.

{% tab template= "chart/user-interaction", es5Template="es5CrossHair" %}

```typescript

import { Chart, LineSeries, Crosshair, DateTime, Legend } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Crosshair, Legend);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
            crosshairTooltip: { enable: true },
        },
        primaryYAxis:
        {
            crosshairTooltip: { enable: true }
        },
        series: [
            {
                type: 'Line', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            }
        ],
        //crosshair for chart
        crosshair: { enable: true },
        legendSettings: { visible: true },
        title: 'Weather Condition'
}, '#element');

```

{% endtab %}

## Customization

The [`fill`](../api/chart/crosshairTooltip/#fill-string) and [`textStyle`](../api/chart/crosshairTooltip/#textstyle-fontmodel)
property of the `crosshairTooltip` is used to customize the background color and font style of the crosshair label respectively.
Color and width of the crosshair line can be customized by using the
[`line`](../api/chart/crosshairSettingsModel/#line-bordermodel) property in the crosshair.

{% tab template= "chart/user-interaction", es5Template="es5CrosshairCust" %}

```typescript

import { Chart, LineSeries, Crosshair, DateTime, Legend } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Crosshair, Legend);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
            crosshairTooltip: { enable: true, fill: 'green' },
        },
        primaryYAxis:
        {
            crosshairTooltip: { enable: true, fill: 'green' },
        },
        series: [
            {
                type: 'Line', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            }
        ],
        crosshair: {
            enable: true,
            // customizing crosshair
            line: {width: 2, color: 'green'} },
        legendSettings: { visible: true },
        title: 'Weather Condition'
}, '#element');

```

{% endtab %}

>Note: To use crosshair feature, we need to inject `Crosshair` module `Chart.Inject(Crosshair)` method.

## Trackball

Trackball is used to track a data point closest to the mouse or touch position. Trackball marker indicates the closest point and trackball tooltip displays the information about the point. To use trackball feature, we need to inject `Crosshair` module and `Tooltip` module using
`Chart.Inject(Crosshair, Tooltip)`.

Trackball can be enabled by setting the [`enable`](../api/chart/crosshairSettings/#enable-boolean) property of the crosshair to true and
[`shared`](../api/chart/tooltipSettings/#shared-boolean) property in `tooltip` to true in chart.

{% tab template= "chart/user-interaction", es5Template="es5Trackball" %}

```typescript

import {  Tooltip, Crosshair, DateTime } from '@syncfusion/ej2-charts';
import { Chart, LineSeries, Legend } from '@syncfusion/ej2-charts';
import { trackData } from './datasource.ts';
Chart.Inject(LineSeries, DateTime, Tooltip, Crosshair, Legend);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                dataSource: trackData, name: 'John', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y'
            },
            {
                dataSource: trackData, name: 'Andrew', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y1'
            },
            {
                dataSource: trackData, name: 'Thomas', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y2'
            },
            {
                dataSource: trackData, name: 'Mark', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y3'
            },
            {
                dataSource: trackData, name: 'William', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y4'
            }
        ],
        // trackball for chart
        tooltip: { enable: true, shared: true, format: '${series.name} : ${point.x} : ${point.y}' },
        crosshair: { enable: true, lineType: 'Vertical' },
        title: 'Average Sales per Person'
}, '#element');

```

{% endtab %}
