---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# To make the scrollbar visible in initial rendering of chart

By setting `zoomFactor` in primaryXAxis and `isZoomed` value as `true` in
[`load`](../../api/chart/chartModel/#load) event and `enableScrollbar` value as `true` in`zoomSettings`, you can make the scrollbar visible in initial rendering of chart.

{% tab template= "chart/how-to", es5Template="es5Scrollbar" %}

```typescript

import { Chart, LineSeries, DateTime, Legend, Tooltip, ILoadedEventArgs, ChartTheme, Zoom, ScrollBar } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, Legend, Tooltip, Zoom, ScrollBar);
    let chart: Chart = new Chart({
        primaryXAxis: {
            zoomFactor: 0.3,
            valueType: 'DateTime',
            labelFormat: 'y',
            intervalType: 'Years',
            edgeLabelPlacement:'Shift'
        },
        primaryYAxis:
        {
            labelFormat: '{value}%',
            rangePadding: 'None',
            minimum: 0,
            maximum: 100,
            interval: 20,
        },
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2005, 0, 1), y: 21 },
                    { x: new Date(2006, 0, 1), y: 24 },
                    { x: new Date(2007, 0, 1), y: 36 },
                    { x: new Date(2008, 0, 1), y: 38 },
                    { x: new Date(2009, 0, 1), y: 54 },
                    { x: new Date(2010, 0, 1), y: 21 },
                    { x: new Date(2011, 0, 1), y: 24 },
                    { x: new Date(2012, 0, 1), y: 36 },
                    { x: new Date(2013, 0, 1), y: 38 },
                    { x: new Date(2014, 0, 1), y: 54 },
                    { x: new Date(2015, 0, 1), y: 21 },
                    { x: new Date(2016, 0, 1), y: 24 },
                    { x: new Date(2017, 0, 1), y: 36 },
                    { x: new Date(2018, 0, 1), y: 38 },
                ],
                xName: 'x', width: 2, marker: {
                    visible: true,
                    width: 10,
                    height: 10
                },
                yName: 'y', name: 'Germany',
            }
        ],
         zoomSettings:
                        {
                             enableMouseWheelZooming: true,
                             enablePinchZooming: true,
                             enableSelectionZooming: true,
                             mode: 'X',
                             enableScrollbar: true,
                        },
        title: 'Inflation - Consumer Price',
        tooltip: {
            enable: true
        },
        load: (args: ILoadedEventArgs) => {
              args.chart.zoomModule.isZoomed = true;
        }
    });
    chart.appendTo('#element');
```

{% endtab %}