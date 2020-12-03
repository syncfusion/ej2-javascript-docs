---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Customize each shape in legend

By using the [`legendRender`](../../api/chart/chartModel/#legendrender), you can customize the legend shape.

To Customize the legend shape, follow the given steps:

**Step 1**:

Set the shape value for each legend using `args.shape` in [`legendRender`](../../api/chart/chartModel/#legendrender) event.

{% tab template= "chart/how-to", es5Template="es5LegendCustom" %}

```typescript

import { Chart, StepAreaSeries, Legend, ILoadedEventArgs, ILegendRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(StepAreaSeries, Legend);
    let chart: Chart = new Chart({
      //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Double',
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Production (Billion as kWh)',
            valueType: 'Double'
        },
        //Initializing Chart Series
        series: [
            {
                type: 'StepArea',
                dataSource: [{ x: 2000, y: 416 }, { x: 2001, y: 490 }, { x: 2002, y: 470 }, { x: 2003, y: 500 },
                { x: 2004, y: 449 }, { x: 2005, y: 470 }, { x: 2006, y: 437 }, { x: 2007, y: 458 }],
                name: 'Renewable',
                xName: 'x', width: 2,
                yName: 'y',
            },
            {
                type: 'StepArea',
                dataSource: [{ x: 2000, y: 180 }, { x: 2001, y: 240 }, { x: 2002, y: 370 }, { x: 2003, y: 200 },
                { x: 2004, y: 229 }, { x: 2005, y: 210 }, { x: 2006, y: 337 }, { x: 2007, y: 258 }],
                name: 'Non-Renewable',
                xName: 'x', width: 2,
                yName: 'y',
            },
        ],
        //Initializing Chart title
    title: 'Electricity- Production',
    legendRender: (args: ILegendRenderEventArgs)=> {
    if (args.text === 'Renewable') {
    args.shape = 'Circle';
    } else if (args.text === 'Non-Renewable') {
    args.shape = 'Triangle';
    }
    },
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{% endtab %}
