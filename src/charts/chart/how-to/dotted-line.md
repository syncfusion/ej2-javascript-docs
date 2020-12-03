---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# To add dotted line using annotation

By using `annotation`, you can add dotted lines in the chart.

To add dotted lines in the chart, follow the given steps:

**Step 1**:

Initialize the custom elements by using the `annotation` property.

By setting `coordinateUnits` value as `point` in annotation object you can placed dotted lines
in the chart based on point x and y values.

{% tab template= "chart/chart-appearance", es5Template="es5Annotationdotted" %}

```typescript

import { Chart, LineSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(LineSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
     primaryYAxis: {
      title: 'Medals'
    },
    annotations:[{
        content: '<div id ="test" style="border-top:3px dashed grey;border-top-width: 2px; width: 10000px"></div>',
        x: 'France',
        y: 50,
        coordinateUnits: 'Point',
        Region: 'Chart'
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Line'
    }],

}, '#element');

```

{% endtab %}