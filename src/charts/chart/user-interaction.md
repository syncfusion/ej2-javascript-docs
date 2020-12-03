
# User Interaction

<!-- markdownlint-disable MD036 -->

## Tooltip

<!-- markdownlint-disable MD036 -->

Chart will display details about the points through tooltip, when the mouse is moved over the point.

**Enable Tooltip for Data Point**

By default, tooltip is not visible. Enable the tooltip by setting
[`enable`](../api/chart/tooltipSettings/#enable) property to true and by injecting `Tooltip` module
using `Chart.Inject(Tooltip)`.

{% tab template= "chart/user-interaction", es5Template="es5Tooltip" %}

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
        title: 'Unemployment Rates 1975-2010',
        //Tooltip for chart
        tooltip: {enable: true}
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD013 -->

**Format the Tooltip**

<!-- markdownlint-disable MD013 -->

By default, tooltip shows information of x and y value in points. In addition to that, you can show more information in tooltip. For example the format `${series.name} ${point.x}` shows series name and point x value.

{% tab template= "chart/user-interaction", es5Template="es5FormatTooltip" %}

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
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            //tooltip format for chart
            format: '${series.name} ${point.x} : ${point.y}'
        }
}, '#element');

```

{% endtab %}

**Tooltip Template**

Any HTML elements can be displayed in the tooltip by using the ‘template’ property of the tooltip. You can use the ${x} and ${y} as place holders in the HTML element to display the x and y values of the corresponding data point.

{% tab template= "chart/user-interaction", es5Template="es5TemplateTooltip" %}

```typescript

import { Chart, StepLineSeries, Legend, Tooltip } from '@syncfusion/ej2-charts';
Chart.Inject(StepLineSeries, Legend, Tooltip);

let chartData: any[] = [
    { x: 1975, y: 16, y1: 10, y2: 4.5 },
    { x: 1980, y: 12.5, y1: 7.5, y2: 5 },
    { x: 1985, y: 19, y1: 11, y2: 6.5 },
    { x: 1990, y: 14.4, y1: 7, y2: 4.4 },
    { x: 1995, y: 11.5, y1: 8, y2: 5 },
    { x: 2000, y: 14, y1: 6, y2: 1.5 },
    { x: 2005, y: 10, y1: 3.5, y2: 2.5 },
    { x: 2010, y: 16, y1: 7, y2: 3.7 }
];
let chart: Chart = new Chart({
        primaryXAxis: {
            title: 'Years',
            lineStyle: { width: 0 },
            minimum: 1975,
            maximum: 2010,
            interval: 5,
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
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            //tooltip template for chart
            template: '<div>${x}</div><div>${y}</div>'
        }
}, '#element');

```

{% endtab %}

**Customize the Appearance of Tooltip**

The [`fill`](../api/chart/tooltipSettings/#fill) and [`border`](../api/chart/tooltipSettings/#border) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](../api/chart/tooltipSettings/#textstyle) property in the tooltip is used to customize the font of the tooltip text.

{% tab template= "chart/user-interaction", es5Template="es5ApperanceTooltip" %}

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
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            format: '${series.name} ${point.x} : ${point.y}',
            //fill for tooltip
            fill: '#7bb4eb',
            //border for tooltip
            border: {
                width: 2,
                color: 'grey'
            }
        }
}, '#element');

```

{% endtab %}

## Zooming  and Panning

**Enable Zooming**

Chart can be zoomed in three ways.

* Selection - By setting [`enableSelectionZooming`](../api/chart/zoomSettingsModel/#enableselectionzooming) property to true
  in `zoomSettings`, you can zoom the chart by using the rubber band selection.
* Mousewheel - By setting [`enableMouseWheelZooming`](../api/chart/zoomSettingsModel/#enablemousewheelzooming) property to true
  in `zoomSettings`, you can zoomin and zoomout the chart by scrolling the mouse wheel.
* Pinch - By setting  [`enablePinchZooming`](../api/chart/zoomSettingsModel/#enablepinchzooming) property to true in `zoomSettings`,
  you can zoom the chart through pinch gesture in touch enabled devices.

>Pinch zooming is supported only in browsers that support multi-touch gestures. Currently IE11, Chrome and Opera browsers support multi-touch in desktop devices.

{% tab template= "chart/user-interaction", es5Template="es5Zooming" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);

let series1: Object[] = [];
let point1: Object;
let value: number = 80;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}
let chart: Chart = new Chart({

        chartArea : {border : {width : 0}},
        primaryXAxis: {
            title: 'Years',
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            edgeLabelPlacement: 'Shift',
            majorGridLines : { width : 0 }
        },
        primaryYAxis:
        {
            title: 'Profit ($)',
            rangePadding: 'None',
            lineStyle : { width: 0 },
            majorTickLines : {width : 0}
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

**Modes of Zooming**

The [`mode`](../api/chart/zoomSettingsModel/#mode) property in zoomSettings specifies whether the chart is allowed to scale along the horizontal axis or vertical axis. The default value of the mode is XY (both axis).

There are three types of mode.

* X- Allows us to zoom the chart horizontally.
* Y - Allows us to zoom the chart vertically.
* XY – Allows us to zoom the chart both vertically and horizontally.

{% tab template= "chart/user-interaction", es5Template="es5ZoomMode" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);

let series1: Object[] = [];
let point1: Object;
let value: number = 80;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}
let chart: Chart = new Chart({

        chartArea : {border : {width : 0}},
        primaryXAxis: {
            title: 'Years',
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            edgeLabelPlacement: 'Shift',
            majorGridLines : { width : 0 }
        },
        primaryYAxis:
        {
            title: 'Profit ($)',
            rangePadding: 'None',
            lineStyle : { width: 0 },
            majorTickLines : {width : 0}
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

**Customizing Zooming Toolbar**

By default, zoomin, zoomout, pan and reset buttons will be displayed for zoomed chart. You can customize to show your desire tools in the toolbar using [`toolbarItems`](../api/chart/zoomSettingsModel/#toolbaritems) property.

{% tab template= "chart/user-interaction", es5Template="es5ZoomToolbar" %}

```typescript

import { Chart, AreaSeries, Legend, Zoom, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(AreaSeries, DateTime, Legend, Zoom);

let series1: Object[] = [];
let point1: Object;
let value: number = 80;
let i: number;
for (i = 1; i < 500; i++) {
    if (Math.random() > .5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    point1 = { x: new Date(1950, i + 2, i), y: value.toFixed(1) };
    series1.push(point1);
}
let chart: Chart = new Chart({

        chartArea : {border : {width : 0}},
        primaryXAxis: {
            title: 'Years',
            valueType: 'DateTime',
            labelFormat: 'yMMM',
            edgeLabelPlacement: 'Shift',
            majorGridLines : { width : 0 }
        },
        primaryYAxis:
        {
            title: 'Profit ($)',
            rangePadding: 'None',
            lineStyle : { width: 0 },
            majorTickLines : {width : 0}
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

>Note: To use zooming feature, we need to inject `Zoom` module `Chart.Inject(Zoom)` method.

## Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

**Enable Crosshair**

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairSettingsModel/#enable) property in the `crosshair`. Likewise tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel/#enable) property of `crosshairTooltip` in the corresponding axis.

{% tab template= "chart/user-interaction", es5Template="es5CrossHair" %}

```typescript

import { Chart, LineSeries, Crosshair, DateTime, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Crosshair, Legend);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let point2: Object;
let value: number = 60;
let value1: number = 50;
let i: number;
for (i = 1; i < 250; i++) {
    if (Math.random() > .5) {
        value += Math.random();
        value1 += Math.random();
    } else {
        value -= Math.random();
        value1 -= Math.random();
    }
    point1 = { x: new Date(2000, i, 1), y: value };
    point2 = { x: new Date(2000, i, 1), y: value1 };
    series1.push(point1);
    series2.push(point2);
}
let chart: Chart = new Chart({
        primaryXAxis: {
            majorGridLines: { width: 0 },
            valueType: 'DateTime',
            crosshairTooltip: { enable: true },
            labelFormat: 'yMMM'
        },
        primaryYAxis:
        {
            minimum: 10, maximum: 90, interval: 10,
            title: 'Temperature (°F)',
            rowIndex: 0,
            crosshairTooltip: { enable: true }
        },
        axes: [
            {
                majorGridLines: { width: 0 },
                rowIndex: 0, opposedPosition: true,
                minimum: 0, maximum: 160, interval: 20,
                name: 'yAxis', title: 'Rainfall (MM)',
                crosshairTooltip: { enable: true }
            }
        ],
        series: [
            {
                type: 'Line', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            },
            {
                type: 'Line', name: 'Rainfall', width: 2,
                dataSource: series2, xName: 'x', yName: 'y',
                yAxisName: 'yAxis'
            }
        ],
        //crosshair for chart
        crosshair: { enable: true },
        legendSettings: { visible: true },
        title: 'Weather Condition'
}, '#element');

```

{% endtab %}

**Customization**

The [`fill`](../api/chart/crosshairTooltipModel/#fill) and [`textStyle`](../api/chart/crosshairTooltipModel/#textstyle)
prop property of the `crosshairTooltip` is used to customize the background color and font style of the crosshair label respectively.
Color and width of the crosshair line can be customized by using the
[`line`](../api/chart/crosshairSettingsModel/#line) property in the crosshair.

{% tab template= "chart/user-interaction", es5Template="es5CrosshairCust" %}

```typescript

import { Chart, LineSeries, Crosshair, DateTime, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Crosshair, Legend);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let point2: Object;
let value: number = 60;
let value1: number = 50;
let i: number;
for (i = 1; i < 250; i++) {
    if (Math.random() > .5) {
        value += Math.random();
        value1 += Math.random();
    } else {
        value -= Math.random();
        value1 -= Math.random();
    }
    point1 = { x: new Date(2000, i, 1), y: value };
    point2 = { x: new Date(2000, i, 1), y: value1 };
    series1.push(point1);
    series2.push(point2);
}
let chart: Chart = new Chart({
        primaryXAxis: {
            majorGridLines: { width: 0 },
            valueType: 'DateTime',
            crosshairTooltip: { enable: true, fill: 'green' },
            labelFormat: 'yMMM'
        },
        primaryYAxis:
        {
            minimum: 10, maximum: 90, interval: 10,
            title: 'Temperature (°F)',
            rowIndex: 0,
            crosshairTooltip: { enable: true, fill: 'green' },
        },
        axes: [
            {
                majorGridLines: { width: 0 },
                rowIndex: 0, opposedPosition: true,
                minimum: 0, maximum: 160, interval: 20,
                name: 'yAxis', title: 'Rainfall (MM)',
                crosshairTooltip: { enable: true, fill: 'green' },
            }
        ],
        series: [
            {
                type: 'Line', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            },
            {
                type: 'Line', name: 'Rainfall', width: 2,
                dataSource: series2, xName: 'x', yName: 'y',
                yAxisName: 'yAxis'
            }
        ],
        crosshair: {
            enable: true,
            //customizing crosshair
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

Trackball can be enabled by setting the [`enable`](../api/chart/crosshairSettingsModel/#enable) property of the crosshair to true and
[`shared`](../api/chart/tooltipSettingsModel/#shared) property in `tooltip` to true in chart.

{% tab template= "chart/user-interaction", es5Template="es5Trackball" %}

```typescript

import {  Tooltip, Crosshair, DateTime } from '@syncfusion/ej2-charts';
import { Chart, LineSeries, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Tooltip, Crosshair, Legend);

let chartData: Object[] = [
    { x: new Date(2000, 2, 11), y: 15, y1: 39, y2: 60, y3: 75, y4: 85 },
    { x: new Date(2000, 9, 14), y: 20, y1: 30, y2: 55, y3: 75, y4: 83 },
    { x: new Date(2001, 2, 11), y: 25, y1: 28, y2: 48, y3: 68, y4: 85 },
    { x: new Date(2001, 9, 16), y: 21, y1: 35, y2: 57, y3: 75, y4: 87 },
    { x: new Date(2002, 2, 7), y: 13, y1: 39, y2: 62, y3: 71, y4: 82 },
    { x: new Date(2002, 9, 7), y: 18, y1: 41, y2: 64, y3: 69, y4: 74 },
    { x: new Date(2003, 2, 11), y: 24, y1: 45, y2: 57, y3: 81, y4: 73 },
    { x: new Date(2003, 9, 14), y: 23, y1: 48, y2: 53, y3: 84, y4: 75 },
    { x: new Date(2004, 2, 6), y: 19, y1: 54, y2: 63, y3: 85, y4: 73 },
    { x: new Date(2004, 9, 6), y: 31, y1: 55, y2: 50, y3: 87, y4: 60 },
    { x: new Date(2005, 2, 11), y: 39, y1: 57, y2: 66, y3: 75, y4: 48 },
    { x: new Date(2005, 9, 11), y: 50, y1: 60, y2: 65, y3: 70, y4: 55 },
    { x: new Date(2006, 2, 11), y: 24, y1: 60, y2: 79, y3: 85, y4: 40 }
];
let chart: Chart = new Chart({
        primaryXAxis: {
            title: 'Years',
            minimum: new Date(2000, 1, 1), maximum: new Date(2006, 2, 11),
            intervalType: 'Years',
            valueType: 'DateTime',
            lineStyle: { width: 0 },
            majorGridLines: { width: 0 },
            edgeLabelPlacement: 'Shift'
        },
        primaryYAxis:
        {
            title: 'Revenue in Millions',
            labelFormat: '{value}M',
            majorTickLines: { width: 0 },
            minimum: 10, maximum: 90,
            lineStyle: { width: 0 }
        },
        series: [
            {
                dataSource: chartData, name: 'John', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y'
            },
            {
                dataSource: chartData, name: 'Andrew', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y1'
            },
            {
                dataSource: chartData, name: 'Thomas', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y2'
            },
            {
                dataSource: chartData, name: 'Mark', xName: 'x',
                marker: { visible: true },
                type: 'Line', width: 2,
                yName: 'y3'
            },
            {
                dataSource: chartData, name: 'William', xName: 'x',
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

## Selection

Chart provides selection support for the series and its data points on mouse click.

>When Mouse is clicked on the data points, the corresponding series legend also will be selected.

We have different types of selection mode for selecting a data.

* None
* Point
* Series
* Cluster
* DragXY
* DragX
* DragY

**Point**

You can select a point, by setting `selectionMode` to point.

{% tab template= "chart/user-interaction", es5Template="es5PointSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
    // selection mode as point
    selectionMode: 'Point',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Series**

You can select a series, by setting `selectionMode` to series.

{% tab template= "chart/user-interaction", es5Template="es5SeriesSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
    // selection mode as series
    selectionMode: 'Series',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Cluster**

You can select the points that corresponds to the same index in all the series, by setting `selectionMode` to cluster.

{% tab template= "chart/user-interaction", es5Template="es5ClusterSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
    // selection mode as cluster
    selectionMode: 'Cluster',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**DragXY, DragX and DragY**

To fetch a collection of data under a particular region, you have to set `selectionMode` as `DragXY`.

* DragXY - Allow us to select data with respect to both horizontal and vertical axis.
* DragX - Allow us to select data with respect to horizontal axis.
* DragY - Allow us to select data with respect to vertical axis.

The selected data’s are returned as an array collection in the
[`dragComplete`](../api/chart/chartModel/#dragcomplete) event.

{% tab template= "chart/user-interaction", es5Template="es5DragSelect" %}

```typescript

import { Chart, ScatterSeries, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ScatterSeries, Legend, Selection);

let series1: Object[] = [];
let series2: Object[] = [];
let point1: Object;
let value: number = 80;
let value1: number = 70;
let i: number;
for (i = 1; i < 120; i++) {
    if (Math.random() > 0.5) {
        value += Math.random();
    } else {
        value -= Math.random();
    }
    value = value < 60 ? 60 : value > 90 ? 90 : value;
    point1 = { x: 120 + (i / 2), y: value.toFixed(1) };
    series1.push(point1);
}
for (i = 1; i < 120; i++) {
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
    primaryXAxis: {
        title: 'Height (cm)',
        minimum: 120, maximum: 180,
        edgeLabelPlacement: 'Shift',
        labelFormat: '{value}cm'
    },
    primaryYAxis:
    {
        title: 'Weight (kg)',
        minimum: 60, maximum: 90,
        labelFormat: '{value}kg',
        rangePadding: 'None'
    },
    series: [
        {
            type: 'Scatter',
            dataSource: series1, xName: 'x', yName: 'y',
            name: 'Male', opacity : 0.7,
            marker: { width: 10, height: 10 }
        }, {
            type: 'Scatter',
            dataSource: series2, xName: 'x', yName: 'y',
            name: 'Female', opacity : 0.7,
            marker: { width: 10, height: 10 }
        }
    ],
    // selection mode as dragxy
    selectionMode: 'DragXY',
    title: 'Height Vs Weight'
}, '#element');

```

{% endtab %}

**Selection Type**

You can select multiple points or series, by enabling the [`isMultiSelect`](../api/chart/chartModel/#ismultiselect)
property.

{% tab template= "chart/user-interaction", es5Template="es5SelectionType" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
    selectionMode: 'Point',
    // multipselect forselection
    isMultiSelect: true,
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Customizing Selection Style**

You can apply custom style to selected points or series with [`selectionStyle`](../api/chart/series/#selectionstyle) property.

{% tab template= "chart/user-interaction", es5Template="es5SelectionStyle" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
        name: 'Gold', type: 'Column',
        //Selection style for chart series selection
        selectionStyle: 'chartSelection1'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        selectionStyle: 'chartSelection2'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        selectionStyle: 'chartSelection3'
    }],
    selectionMode: 'Point',
    isMultiSelect: true,
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

**Selection on Load**

You can able to select a point or series programmatically on a chart using
[`selectedDataIndexes`](../api/chart/chartModel/#selecteddataindexes) property.

{% tab template= "chart/user-interaction", es5Template="es5Load" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
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
        name: 'Gold', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection1'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection2'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection3'
    }],
    selectionMode: 'Point',
    isMultiSelect: true,
    // Selcted data indexes for chart series
    selectedDataIndexes: [
        { series: 0, point: 1}, { series: 2, point: 3}
    ],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}
