---
title: " RangeNavigator Export and Print | TypeScript "

component: "RangeNavigator"

description: "The rendered rangenavigator can be printed or exported directly from the browser by calling the public method print and export."
---

# Export and print

## Export

The rendered range navigator can be exported to JPEG, PNG, SVG, or PDF format using the export method in the range navigator. The input parameters for this method are Export Type for format and fileName for result.

{% tab template= "rangenavigator/export-print", es5Template="es5default" %}

```typescript

import { SplineSeries, AreaSeries, DateTime, Crosshair } from '@syncfusion/ej2-charts';
import { RangeNavigator, Chart, IChangedEventArgs } from '@syncfusion/ej2-charts';
import {  RangeTooltip, Tooltip } from '@syncfusion/ej2-charts';
import { bitCoinData } from './datasource.ts';
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);

let range: RangeNavigator = new RangeNavigator(
    {
        valueType: 'DateTime',
        value: [new Date(2017, 8, 1), new Date(2018, 1, 1)],
        tooltip: { enable: true },
        series: [
            {
                dataSource: bitCoinData, xName: 'x', yName: 'y', type: 'Area',
                width: 2, animation: { enable: false }
            }
        ],
    }
);
range.appendTo('#element');

 document.getElementById('export').onclick = () => {
        range.export('PNG', 'result',  null, [range]);
    };


```

{% endtab %}

## Print

The rendered range navigator can be printed directly from the browser by calling the public method print. The ID of the range navigator div element must be passed as argument to that method.

{% tab template= "rangenavigator/print", es5Template="es5default" %}

```typescript

import { SplineSeries, AreaSeries, DateTime, Crosshair } from '@syncfusion/ej2-charts';
import { RangeNavigator, Chart, IChangedEventArgs } from '@syncfusion/ej2-charts';
import {  RangeTooltip, Tooltip } from '@syncfusion/ej2-charts';
import { bitCoinData } from './datasource.ts';
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);

let range: RangeNavigator = new RangeNavigator(
    {
        valueType: 'DateTime',
        value: [new Date(2017, 8, 1), new Date(2018, 1, 1)],
        tooltip: { enable: true },
        series: [
            {
                dataSource: bitCoinData, xName: 'x', yName: 'y', type: 'Area',
                width: 2, animation: { enable: false }
            }
        ],
    }
);
range.appendTo('#element');

  document.getElementById('print').onclick = () => {
        range.print();
    };


```

{% endtab %}
