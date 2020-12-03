---
title: " Chart Tooltip | TypeScript "

component: "Chart"

description: "Tooltip is used to show the data value when mouse hover on the chart.We can able to customize format,template and appearance."
---

# Tooltip

<!-- markdownlint-disable MD036 -->

Chart will display details about the points through tooltip, when the mouse is moved over the point.

## Default Tooltip

By default, tooltip is not visible. Enable the tooltip by setting
[`enable`](https://ej2.syncfusion.com/documentation/api/chart/tooltipSettingsModel#enable-boolean) property to true and by injecting `Tooltip` module
using `Chart.Inject(Tooltip)`.

{% tab template= "chart/user-interaction", es5Template="es5Tooltip" %}

```typescript

import { Chart, StepLineSeries, DateTime, Tooltip } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
Chart.Inject(StepLineSeries, DateTime, Tooltip);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime'
        },
        series: [
            {
                type: 'StepLine',
                dataSource: chartData, xName: 'x', yName: 'y',
                width: 2, name: 'China',
                marker: {
                    visible: true, width: 10, height: 10
                },
            }],
        title: 'Unemployment Rates 1975-2010',
        //Default tooltip for chart
        tooltip: {enable: true}
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD013 -->

## Format the Tooltip

<!-- markdownlint-disable MD013 -->

By default, tooltip shows information of x and y value in points. In addition to that, you can show more information in tooltip. For example the format `${series.name} ${point.x}` shows series name and point x value.

{% tab template= "chart/user-interaction", es5Template="es5FormatTooltip" %}

```typescript

import { Chart, SplineSeries, DateTime, Tooltip } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
Chart.Inject(SplineSeries, DateTime, Tooltip);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Spline',
                dataSource: chartData, xName: 'x', yName: 'y',
                width: 2, name: 'China',
                marker: {
                    visible: true, width: 10, height: 10
                },
            }
        ],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            //tooltip format for chart
             header: 'Unemployment',
             format: '<b>${point.x} : ${point.y}</b>'
        }
}, '#element');

```

{% endtab %}

## Tooltip Template

Any HTML elements can be displayed in the tooltip by using the ‘template’ property of the tooltip. You can use the ${x} and ${y} as place holders in the HTML element to display the x and y values of the corresponding data point.

{% tab template= "chart/user-interaction", es5Template="es5TemplateTooltip" %}

```typescript

import { Chart, StepLineSeries, Legend, Tooltip } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
Chart.Inject(StepLineSeries, Legend, Tooltip);

let chart: Chart = new Chart({
        series: [
            {
                type: 'StepLine',
                dataSource: data, xName: 'x', yName: 'y',
                width: 2, name: 'China',
                marker: {
                    visible: true, width: 10, height: 10
                },
            }
        ],
        title: 'Unemployment Rates 1975-2010',
        tooltip: {
            enable: true,
            //tooltip template for chart
            template: '#Unemployment'
        }
}, '#element');

```

{% endtab %}

## Customize the Appearance of Tooltip

The [`fill`](https://ej2.syncfusion.com/documentation/api/chart/tooltipSettingsModel#fill-string) and [`border`](https://ej2.syncfusion.com/documentation/api/chart/tooltipSettingsModel#border-bordermodel) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](https://ej2.syncfusion.com/documentation/api/chart/tooltipSettingsModel#textstyle-fontmodel) property in the tooltip is used to customize the font of the tooltip text.

{% tab template= "chart/user-interaction", es5Template="es5ApperanceTooltip" %}

```typescript

import { Chart, StepLineSeries, DateTime, Legend, Tooltip } from '@syncfusion/ej2-charts';
import { chartData } from './datasource.ts';
Chart.Inject(StepLineSeries, DateTime, Legend, Tooltip);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'StepLine',
                dataSource: chartData, xName: 'x', yName: 'y',
                width: 2, name: 'China',
                marker: {
                    visible: true, width: 10, height: 10
                },
            }
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

## See Also

* [Format the tooltip value](./how-to/tool-tip-format.md)
* [Create a table in tooltip](./how-to/tool-tip-table#create-a-table-in-tooltip.md)