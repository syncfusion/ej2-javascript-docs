---
title: " Chart Internationalization | TypeScript "

component: "Chart"

description: "Chart provides the support for internationalization for dataLabel, axis label and tooltip elements."
---

# Internationalization

Chart provide supports for internationalization for below chart elements.

* Datalabel.
* Axis label.
* Tooltip.

For more information about number and date formatter you can refer
[`internationalization`](https://ej2.syncfusion.com/documentation/common/internationalization/).

<!-- markdownlint-disable MD036 -->
**Globalization**

Globalization is the process of designing and developing an component that works in different
cultures/locales.  Internationalization  library is used to globalize number, date, time values in
Chart component using  `labelFormat` property in axis.

**Numeric Format**

  In the below example axis, point  and tooltip labels are globalized to EUR.

{% tab template= "chart/internationalization", es5Template="es5International" %}

```typescript

import { Chart, ColumnSeries, DataLabel, Tooltip } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Tooltip);
import { loadCldr, L10n, setCulture, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture('de');
setCurrencyCode('EUR');
let chartData: any[] = [
    { x: 1900, y: 4, y1: 2.6 }, { x: 1920, y: 3.0, y1: 2.8 },
    { x: 1940, y: 3.8, y1: 2.6}, { x: 1960, y: 3.4, y1: 3 },
    { x: 1980, y: 3.2, y1: 3.6 }, { x: 2000, y: 3.9, y1: 3 }
]
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Year',
        edgeLabelPlacement: 'Shift'
    },
    primaryYAxis: {
        title: 'Sales Amount in Millions',
        //Label format as currency
        labelFormat: 'c'
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Column',
        marker: { dataLabel: { visible: true }}
    },{
        dataSource: chartData,
        xName: 'x', yName: 'y1',
        name: 'Product Y', type: 'Column',
         marker: { dataLabel: { visible: true }}
    }],
    title: 'Average Sales Comparison',
    tooltip: { enable: true, format: '${series.name} <br>${point.x} : ${point.y}'}
}, '#element');

```

{% endtab %}