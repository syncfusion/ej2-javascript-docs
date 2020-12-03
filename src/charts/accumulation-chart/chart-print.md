---
title: " Accumulation Chart Print and Export | TypeScript "

component: "Accumulation Chart"

description: "Accumultion chart have a public methods for print or export the rendered chart"
---

# Print and Export

## Print

The rendered chart can be printed directly from the browser by calling the public method print.

{% tab template= "chart/print" , es5Template="es5AccPrint"%}

```typescript

import { AccumulationChart }  from '@syncfusion/ej2-charts';

let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            radius: '100%',
            xName: 'x',
            yName: 'y'
        }
    ]
}, '#element');


    document.getElementById('print').onclick = () => {
        piechart.print();
    };

```

{% endtab %}

## Export

The rendered chart can be exported to `Image`(jpeg or png) or `SVG` or `PDF` format by using the export method.
Input parameters for this method are `Export` Type for `format` and `fileName` of result.

{% tab template= "chart/print", es5Template="es5AccExport" %}

```typescript

import { AccumulationChart,Export }  from '@syncfusion/ej2-charts';
AccumulationChart.Inject(Export);

let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            radius: '100%',
            xName: 'x',
            yName: 'y'
        }
    ]
}, '#element');


    document.getElementById('print').onclick = () => {
        piechart.exportModule.export('PNG', 'result');
    };

```

{% endtab %}
