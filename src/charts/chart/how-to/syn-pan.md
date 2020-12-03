---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Synchronize panning between multiple charts

Using the [`chartMouseMove`](../../api/chart/chartModel/#chartmousemove) event, you can achieve the synchronized panning between multiple charts.

To make a synchronized panning chart, follow the given steps:

**Step 1**:

Initially create two charts, and enable `zoomSettings` for both charts.

To use the [`chartMouseMove`](../../api/chart/chartModel/#chartmousemove) event, assign the first chart's `zoomFactor` and `zoomPosition` values to the second chart. Now, pan the first zoomed chart, and then the second chart will be panned automatically based on `zoomFactor` and `zoomPosition`.

The following code sample demonstrates the output.

{% tab template= "chart/chart-appearance", es5Template="es5sync" %}

```typescript

import { ChartTheme, Chart, LineSeries, DateTime, Legend, DataLabel,
IMouseEventArgs,Zoom } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Legend, DataLabel,Zoom);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'DateTime',
            labelFormat: 'y/M/d',
            edgeLabelPlacement: 'Shift',

        },
        primaryYAxis:
        {
            minimum: -20,
            maximum: 30,
            interval: 10,
            edgeLabelPlacement: 'Shift',
            labelFormat: '{value}°C',

        },
        width: '450px',
        height:'300px',

        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2016, 3, 1), y: 6.3 },
                    { x: new Date(2016, 4, 1), y: 13.3 }, { x: new Date(2016, 5, 1), y: 18.0 },
                    { x: new Date(2016, 6, 1), y: 19.8 }, { x: new Date(2016, 7, 1), y: 18.1 },
                    { x: new Date(2016, 8, 1), y: 13.1 }, { x: new Date(2016, 9, 1), y: 4.1 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'Warmest',
                marker: {
                    visible: true,
                    height: 10, width: 10,
                    shape: 'Pentagon',
                    dataLabel: { visible: true, position: 'Top' }
                }
            }, {
                type: 'Line',
                dataSource: [
                    { x: new Date(2016, 3, 1), y: -5.3 },
                    { x: new Date(2016, 4, 1), y: 1.0 }, { x: new Date(2016, 5, 1), y: 6.9 },
                    { x: new Date(2016, 6, 1), y: 9.4 }, { x: new Date(2016, 7, 1), y: 7.6 },
                    { x: new Date(2016, 8, 1), y: 2.6 }, { x: new Date(2016, 9, 1), y: -4.9 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'Coldest',
                marker: {
                    visible: true, height: 10, width: 10, shape: 'Diamond',
                    dataLabel: { visible: true, position: 'Bottom' }
                }
            }
        ],
        //Initializing Chart title
        title: 'Alaska Weather Statistics - 2016',
        zoomSettings:{
          enableSelectionZooming: true,
          enableMouseWheelZooming: true,
          enablePinchZooming: true
        },
        chartMouseMove: (args:IMouseEventArgs ) => {
          chart1.primaryXAxis.zoomFactor = chart.primaryXAxis.zoomFactor;
          chart1.primaryXAxis.zoomPosition = chart.primaryXAxis.zoomPosition;
        }
    });
    chart.appendTo('#element');
    let chart1: Chart = new Chart({
        //Initializing Primary X and Y Axis
        primaryXAxis: {
            valueType: 'DateTime',
            labelFormat: 'MMM',
            edgeLabelPlacement: 'Shift',

        },
        primaryYAxis:
        {
            minimum: -20,
            maximum: 30,
            interval: 10,
            edgeLabelPlacement: 'Shift',
            labelFormat: '{value}°C',

        },
        width: '450px',
        height:'300px',

        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2016, 3, 1), y: 6.3 },
                    { x: new Date(2016, 4, 1), y: 13.3 }, { x: new Date(2016, 5, 1), y: 18.0 },
                    { x: new Date(2016, 6, 1), y: 19.8 }, { x: new Date(2016, 7, 1), y: 18.1 },
                    { x: new Date(2016, 8, 1), y: 13.1 }, { x: new Date(2016, 9, 1), y: 4.1 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'Warmest',
                marker: {
                    visible: true,
                    height: 10, width: 10,
                    shape: 'Pentagon',
                    dataLabel: { visible: true, position: 'Top' }
                }
            }, {
                type: 'Line',
                dataSource: [
                    { x: new Date(2016, 3, 1), y: -5.3 },
                    { x: new Date(2016, 4, 1), y: 1.0 }, { x: new Date(2016, 5, 1), y: 6.9 },
                    { x: new Date(2016, 6, 1), y: 9.4 }, { x: new Date(2016, 7, 1), y: 7.6 },
                    { x: new Date(2016, 8, 1), y: 2.6 }, { x: new Date(2016, 9, 1), y: -4.9 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'Coldest',
                marker: {
                    visible: true, height: 10, width: 10, shape: 'Diamond',
                    dataLabel: { visible: true, position: 'Bottom' }
                }
            }
        ],
        zoomSettings:{
          enableMouseWheelZooming: true,
          enablePinchZooming: true,
          enableSelectionZooming: true
        },
        //Initializing Chart title
        title: 'Alaska Weather Statistics - 2017',
        chartMouseMove: (args:IMouseEventArgs ) => {
            chart1.primaryXAxis.zoomFactor = chart.primaryXAxis.zoomFactor;
          chart1.primaryXAxis.zoomPosition = chart.primaryXAxis.zoomPosition;
        }
    });
    chart1.appendTo('#element1');

```

{% endtab %}