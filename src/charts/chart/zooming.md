---
title: " Chart Zooming | TypeScript "

component: "Chart"

description: "Chart have zooming and panning properties. Chart contains different  zoom modes, zoom toolbar items, scrollbar and auto interval zooming. "
---

# Zooming  and Panning

## Enable Zooming

Chart can be zoomed in three ways.

* Selection - By setting [`enableSelectionZooming`](../api/chart/zoomSettingsModel/) property to true
  in `zoomSettings`, you can zoom the chart by using the rubber band selection.
* Mousewheel - By setting [`enableMouseWheelZooming`](../api/chart/zoomSettingsModel/) property to true
  in `zoomSettings`, you can zoomin and zoomout the chart by scrolling the mouse wheel.
* Pinch - By setting  [`enablePinchZooming`](../api/chart/zoomSettingsModel/) property to true in `zoomSettings`,
  you can zoom the chart through pinch gesture in touch enabled devices.

>Pinch zooming is supported only in browsers that support multi-touch gestures. Currently IE11, Chrome and Opera browsers support multi-touch in desktop devices.

{% tab template= "chart/user-interaction", es5Template="es5Zooming" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        //Zooming for chart
        zoomSettings:
        {
            enableMouseWheelZooming: true,
            enablePinchZooming: true,
            enableSelectionZooming: true
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

After zooming the chart, a zooming toolbar will appear with `zoom`,`zoomin`, `zoomout`, `pan` and `reset` buttons.
Selecting the Pan option will allow to pan the chart and selecting the Reset option will reset the zoomed chart.

## Modes

The [`mode`](../api/chart/zoomSettingsModel/) property in zoomSettings specifies whether the chart is allowed to scale along the horizontal axis or vertical axis. The default value of the mode is XY (both axis).

There are three types of mode.

* X- Allows us to zoom the chart horizontally.
* Y - Allows us to zoom the chart vertically.
* XY – Allows us to zoom the chart both vertically and horizontally.

{% tab template= "chart/user-interaction", es5Template="es5ZoomMode" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableSelectionZooming: true,
            //zoom mode as x
            mode: 'X'
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

## Toolbar

By default, zoomin, zoomout, pan and reset buttons will be displayed for zoomed chart. You can customize to show your desire tools in the toolbar using [`toolbarItems`](../api/chart/zoomSettingsModel/) property.

{% tab template= "chart/user-interaction", es5Template="es5ZoomToolbar" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableSelectionZooming: true,
            //toolbar items for zooming toolkit
            toolbarItems: ['Zoom', 'Pan', 'Reset']
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

## Enable pan

Using [`enablePan`](../api/chart/zoomSettingsModel/)
property you can able to pan the zoomed chart without help of toolbar items.

{% tab template= "chart/user-interaction", es5Template="es5ZoomToolbar" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
            zoomFactor: 0.2, zoomPosition: 0.6
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableSelectionZooming: true,
            enablePan: true
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

## Enable Scrollbar

Using `enableScrollbar` property, you can able to add scrollbar for zoomed chart. Using this scrollbar, you can pan or zoom the chart.

{% tab template= "chart/user-interaction", es5Template="es5Scrollbar" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime, ScrollBar } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom, ScrollBar);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableSelectionZooming: true,
            enableScrollbar: true,
            mode:'X'
        },
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

## Auto interval on zooming

By using [`enableAutoIntervalOnZooming`](../api/chart/axis/) property,
the axis interval will get calculated automatically with respect to the zoomed range.

{% tab template= "chart/user-interaction", es5Template="es5ZoomToolbar" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
import { series1 } from './datasource.ts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Area',
                dataSource: series1,
                name: 'Product X',
                xName: 'x',
                yName: 'y',
                border: { width: 0.5, color: '#00bdae' },
                animation: { enable: false }
            },
        ],
        zoomSettings:
        {
            enableSelectionZooming: true,
        },
        enableAutoIntervalOnZooming: true,
        title: 'Sales History of Product X',
        legendSettings: { visible: false },
}, '#element');

```

{% endtab %}

>Note: To use zooming feature, we need to inject `Zoom` module `Chart.Inject(Zoom)` method.
