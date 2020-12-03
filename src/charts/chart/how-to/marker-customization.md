---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Customize the marker with different shape

By using the [`pointRender`](../../api/chart/chartModel/#pointrender), you can customize the marker shape.

To Customize the marker shape, follow the given steps:

**Step 1**:

Customize the marker shape in each data point by using the [`pointRender`](../../api/chart/chartModel/#pointrender) event. Using this event, you can set the `shape` value to the argument.

{% tab template= "chart/how-to", es5Template="es5MarkerCustom" %}

```typescript

import { Chart, LineSeries, Category,IPointRenderEventArgs, Legend,ILoadedEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend);
let shapes: string[] = [
   'Diamond', 'Circle','Rectangle', 'Line', 'Triangle', 'Rectangle'
   ];
let shapeRender: EmitType<IPointRenderEventArgs> = (args: IPointRenderEventArgs)=> {
 args.shape = shapes[args.point.index];
 };
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Countries', valueType: 'Category',
            interval: 1
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Penetration', rangePadding: 'None',
            labelFormat: '{value}%', minimum: 0,
            maximum: 75, interval: 15
        }
        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [{ x: 'WW', y: 12, text: 'World Wide' },
                { x: 'EU', y: 5, text: 'Europe' },
                { x: 'APAC', y: 15, text: 'Pacific' },
                { x: 'LATAM', y: 6.4, text: 'Latin' },
                { x: 'MEA', y: 30, text: 'Africa' },
                { x: 'NA', y: 25.3, text: 'America' }],
                name: 'December 2007',
                marker: {
                    visible: true, width: 10, height: 10,
                    shape: 'Diamond', dataLabel: { name: 'text' }
                },
                xName: 'x', width: 2,
                yName: 'y',
            },

        ],
        //Initializing Chart title
        title: 'FB Penetration of Internet Audience',
        legendSettings: { visible: false },
        pointRender: shapeRender,
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{% endtab %}
