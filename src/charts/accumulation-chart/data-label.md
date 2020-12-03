---
title: " Accumulation Chart Data Label | TypeScript "

component: "Accumulation Chart"

description: "Data labels are names of the data points that are displayed on the x-axis of a chart and also used to highlight important data points"
---

# Data Label

Data label can be added to a chart series by enabling the [`visible`](../api/accumulation-chart/accumulationDataLabelSettingsModel/)
option in the dataLabel property.

{% tab template="chart/chart-types", es5Template="es5AccDataLabelTemplate" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    enableSmartLabels: true,
    series: [
        {
            dataSource: [{ x: 'Jan', y: 13, text: 'Jan: 3' }, { x: 'Feb', y: 13.5, text: 'Feb: 3.5' },
                { x: 'Mar', y: 7, text: 'Mar: 7' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' }],
            xName: 'x',
            yName: 'y',
            dataLabel: { visible: true }
        }
    ]
}, '#element');

```

{% endtab %}

>Note: To use the data label feature, inject the `DataLabel` using the `Chart.Inject(DataLabel)` method.

## Positioning

Accumulation chart provides support for placing the data label either `inside` or `outside` the chart.

{% tab template="chart/chart-types", es5Template="es5AccDataLabelTemplate" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y',
            dataLabel: { visible: true, position:'Outside' }
        }
    ]
}, '#element');

```

{% endtab %}

## Smart Labels

Datalabels will be arranged smartly without overlapping with each other. You can enable or disable this feature using
the [`enableSmartLabels`](../api/accumulation-chart/accumulationChartModel/#enablesmartlabels) property.

{% tab template="chart/chart-types", es5Template="es5AccSmartLabels" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    enableSmartLabels: true,
    series: [
        {
            dataSource: [
                { x: 'Jan', y: 3, text: 'Jan: 3' }, { x: 'Feb', y: 3.5, text: 'Feb: 3.5' },
                { x: 'Mar', y: 7, text: 'Mar: 7' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' },
                { x: 'May', y: 19, text: 'May: 19' }, { x: 'Jun', y: 23.5, text: 'Jun: 23.5' },
                { x: 'Jul', y: 26, text: 'Jul: 26' }, { x: 'Aug', y: 25, text: 'Aug: 25' },
                { x: 'Sep', y: 21, text: 'Sep: 21' }, { x: 'Oct', y: 15, text: 'Oct: 15' }],
            dataLabel: { visible: true, name: 'text', position: 'Outside' },
            xName: 'x',
            yName: 'y'
        }
    ]
}, '#element');

```

{% endtab %}

## Data Label Template

Label content can be formatted by using the template option. Inside the template, you can add the placeholder text
`${point.x}` and `${point.y}` to display corresponding data points x & y value. Using
[`template`](../api/accumulation-chart/accumulationDataLabelSettingsModel/)property, you can set data label
template in chart.

{% tab template="chart/chart-types", es5Template="es5AccDataLabelTemplate" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    enableSmartLabels: true,
    series: [
        {
            dataSource: labelData,
            dataLabel: { visible: true, name: 'text', position: 'Inside',
                template:  "<div id='templateWrap' style='background-color:#bd18f9;border-radius: 3px; float: right;padding: 2px;line-height: 20px;text-align: center;'>"+ "<img src='https://ej2.syncfusion.com/demos/src/chart/images/sunny.png' />" + "<div style='color:white; font-family:Roboto; font-style: medium; fontp-size:14px;float: right;padding: 2px;line-height: 20px;text-align: center;padding-right:6px'><span>${point.y}</span></div></div>"
            },xName: 'x', yName: 'y'
        }]
}, '#element');

```

{% endtab %}

## Connector Line

Connector line will be visible when the data label is placed `outside` the chart.
The connector line can be customized using the `type`, `color`, `width`, `length` and `dashArray` properties

{% tab template="chart/chart-types", es5Template="es5AccSmartLabels" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    enableSmartLabels: true,
    series: [
        {
            dataSource: labelData,
            dataLabel: { visible: true, name: 'text', position: 'Outside',
                connectorStyle:{
                    //Length of the connector line in pixels
                    length: '50px',
                    //Width of the connector line in pixels
                    width: 2,
                    //dashArray of the connector line
                    dashArray: '5,3',
                    //Color of the connector line
                    color: '#f4429e',
                    //Specifies the type of the connector line either Line or Curve
                    type: 'Curve'
                }
            }, xName: 'x', yName: 'y'}
    ]
}, '#element');

```

{% endtab %}

## Text Mapping

Text from the data source can be mapped to data label using `name` property.

{% tab template="chart/chart-types", es5Template="es5AccAngles" %}

```typescript

import { AccumulationChart, AccumulationDataLabel  } from '@syncfusion/ej2-charts';
import { dataMapping } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);

let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource:dataMapping ,
            xName: 'x',
            yName: 'y',
            dataLabel: { visible: true, name:'text' }
        }
    ]
}, '#element');

```

{% endtab %}

## Customization

Individual text can be customized using the `textRender` event.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, FunnelSeries, IAccTextRenderEventArgs, AccumulationDataLabel } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(FunnelSeries, AccumulationDataLabel);
let accChart: AccumulationChart = new AccumulationChart({
   series: [
        {
            dataSource: labelData,
            dataLabel: { visible: true, name: 'text', position: 'Outside' },
            xName: 'x',
            yName: 'y'
        }
    ],

     textRender: (args: IAccTextRenderEventArgs) => {
        if (args.text.indexOf('Mar') > -1) {
            args.color = 'red';
            args.border.width = 1;
        }
    },
}, '#element');

```

{% endtab %}
