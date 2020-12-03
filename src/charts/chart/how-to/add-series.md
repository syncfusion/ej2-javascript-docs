---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and how to access different types properties and events of the chart."
---

# Add or remove a series from the chart dynamically

You can add or remove the chart series dynamically by using the `addSeries` or `removeSeries` method.

To add or remove the series dynamically, follow the given steps:

**Step 1**:

To add a new series to chart dynamically, pass the series value to the `addSeries` method.

To remove the new series from chart dynamically, pass the series index to the `removeSeries` method.

{% tab template= "chart/add-series", es5Template="es5AddSeries" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
import { Button } from '@syncfusion/ej2-buttons';
import { EmitType } from '@syncfusion/ej2-base';

let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Manager',
            valueType: 'Category',

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Column',
                dataSource: [{ x: 'John', y: 10000 }, { x: 'Jake', y: 12000 }, { x: 'Peter', y: 18000 },
                { x: 'James', y: 11000 }, { x: 'Mary', y: 9700 }],
                xName: 'x', width: 2,
                yName: 'y'
            }
        ],
        //Initializing Chart title
        title: 'Sales Comparision',
    }, '#element');

    document.getElementById('add').onclick = () => {
        chart.addSeries([{
                type: 'Column',
                dataSource: [{ x: 'John', y: 11000 }, { x: 'Jake', y: 16000 }, { x: 'Peter', y: 19000 },
                { x: 'James', y: 12000 }, { x: 'Mary', y: 10700 }],
                xName: 'x', width: 2,
                yName: 'y'
            }]);
    };
     document.getElementById('remove').onclick = () => {
        chart.removeSeries(1);
    };
```

{% endtab %}