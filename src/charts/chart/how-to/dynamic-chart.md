---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# To add chart dynamically

By using html button, you can add the chart dynamically when click the button.

To add the chart dynamically through button click, follow the given steps:

**Step 1**:

Initially create the html button.

Then create chart inside of button `onClick` function. Now click the button charts will render based on click count.

The following code sample demonstrates the output.

{% tab template= "chart/dynamic-chart", es5Template="es5sync" %}

```typescript

import { Chart, LineSeries, DateTime, Legend, Tooltip, ILoadedEventArgs, ChartTheme } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
Chart.Inject(LineSeries, DateTime, Legend, Tooltip);


let count: number = 0;  
document.getElementById('btn').onclick=()=> {

      //Create div element dynamically and append to DOM
        var chartEle = document.createElement('div');
        chartEle.id = 'chartContainer' + count;
        document.getElementsByTagName('body')[0].appendChild(chartEle);

        //Created chart here
        var chart = new Chart({
            series: [{
                type: 'Line', xName: 'x', width: 2, marker: { visible: true },
                yName: 'y', name: 'Germany',
                dataSource: [{ x: 1, y: 21 },{ x: 2, y: 24 },{ x: 3, y: 36 },
                        { x: 4, y: 38 },{ x: 5, y: 54 },{ x: 6, y: 57 },{ x: 7, y: 70 }],
                }],
            title: 'Inflation - Consumer Price', tooltip: { enable: true }, height:'400', width: '800'
        });
        chart.appendTo('#' + chartEle.id);
        count++;
}

```

{% endtab %}