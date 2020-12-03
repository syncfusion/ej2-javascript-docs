---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Format the tooltip value

Using [`tooltipRender`](../../api/chart/chartModel/#tooltiprender) event, you can able to format the
datetime value instead of rendered value.

To format the datetime value,please follow the steps below

**Step 1**:

By using [`tooltipRender`](../../api/chart/chartModel/#tooltiprender) event we can able to get
the current point x value. Using this value to format the tooltip by using `formatDate` method.

The output will appear as follows,

{% tab template= "chart/how-to", es5Template="es5TooltipFormat" %}

```typescript
import { Chart, LineSeries, DateTime,  ITooltipRenderEventArgs, DataLabel, Tooltip } from '@syncfusion/ej2-charts';
import { Internationalization } from '@syncfusion/ej2-base';
Chart.Inject(LineSeries, DateTime, DataLabel, Tooltip);
let chart: Chart = new Chart({

        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'DateTime',
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2005, 0, 1), y: 21 }, { x: new Date(2006, 0, 1), y: 24 },
                    { x: new Date(2007, 0, 1), y: 30 }, { x: new Date(2008, 0, 1), y: 38 },
                    { x: new Date(2009, 0, 1), y: 54 }, { x: new Date(2010, 0, 1), y: 57 },
                ],
                xName: 'x', width: 2, marker: {
                  dataLabel : { visible: true },
                    visible: true,
                    width: 10,
                    height: 10
                },
                yName: 'y', name: 'Germany',
            }
        ],

       //Initializing Chart title
        title: 'Inflation - Consumer Price',
        tooltip: {enable: true},
        tooltipRender:(args: ITooltipRenderEventArgs) => {  //  To format the current point x value
        let intl: Internationalization = new Internationalization();
        let formattedString: string = intl.formatDate(new Date(args.point.x), { skeleton: 'yMd' });
        args.text = formattedString;
        };
    width:'650px',
    height: '350px'
},'#element');
```

{% endtab %}