---
title: " Chart Print and Export | TypeScript "

component: "Chart"

description: "The rendered chart can be printed or exported directly from the browser by calling the public method print and export."
---

# Print and Export

## Print

The rendered chart can be printed directly from the browser by calling the public method print. ID of the chart div element must be passed as argument to that method.

{% tab template= "chart/print", es5Template="es5Print" %}

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
            majorGridLines: { width: 0 }

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
            majorGridLines: { width: 0 }
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


    document.getElementById('print').onclick = () => {
        chart.print();
    };

```

{% endtab %}

## Export

The rendered chart can be exported to `JPEG`, `PNG`, `SVG`, or `PDF` format using the export method in chart. The input parameters for this method are `Export Type` for format and `fileName` for result.

The optional parameters for this method are,
* `orientation` - either portrait or landscape,
* `controls` - pass collections of controls for multiple export,
* `width` - width of chart export, and
* `height` - height of chart export.

{% tab template= "chart/export", es5Template="es5Export" %}

```typescript
import { Chart, ColumnSeries, Category, Legend, Export } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Export);
import { EmitType } from '@syncfusion/ej2-base';

let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Manager',
            valueType: 'Category',
            majorGridLines: { width: 0 }

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
            majorGridLines: { width: 0 }
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


    document.getElementById('print').onclick = () => {
        chart.exportModule.export('PNG', 'result');
    };
```

{% endtab %}

## Multiple Chart Export

You can export the multiple charts in single page by passing the multiple chart objects in the export
method of chart.

To export multiple charts in a single page, follow the given steps:

**Step 1**:

Initially, render more than one chart to export, and then add button to export the multiple charts. In
button click, call the export private method in charts, and then pass the multiple chart objects in the
export method.

{% tab template= "chart/export", es5Template="es5multiexport" %}

```typescript
import { Chart, ColumnSeries, Category, Legend,Export } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend,Export);
import { EmitType } from '@syncfusion/ej2-base';

let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Manager',
            valueType: 'Category',
            majorGridLines: { width: 0 }

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
            majorGridLines: { width: 0 }
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
    let chart1: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Manager',
            valueType: 'Category',
            majorGridLines: { width: 0 }

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
            majorGridLines: { width: 0 }
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
    }, '#element1');

    document.getElementById('print').onclick = () => {
        chart.exportModule.export('PNG', Chart, null, [chart, chart1]);;
    };

```

{% endtab %}