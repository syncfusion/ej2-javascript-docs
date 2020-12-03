---
title: " Accumulation Chart Empty Points | TypeScript "

component: "Accumulation Chart"

description: "Empty data points are useful for controlling the appearance and structure the chart's data as well as handling points whose data is a null value"
---

# Empty Points

The data points those uses the `null` or `undefined` as value are considered as empty points. The empty data points
are ignored and not plotted in the chart. You can customize those points, using the `emptyPointSettings` property in
series. The default mode of the empty point is `Gap`. Other supported modes are `Average` and `Zero`.

{% tab template="chart/chart-types", es5Template="es5AccEmpty" %}

```typescript

import { AccumulationChart, AccumulationDataLabel } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationDataLabel);

let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: undefined }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: null }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            xName: 'x',
            yName: 'y',
            emptyPointSettings: { mode: 'Zero', fill: 'pink'},
            dataLabel: { visible: true, position: 'Outside' }
        }
    ]
}, '#element');

```

{% endtab %}

## Customization

Specific color for an empty point can be set by using the `fill` property in `emptyPointSettings` and the
border for an empty point can be set by using the `border` property.

{% tab template="chart/chart-types", es5Template="es5AccEmptyCust" %}

```typescript

import { AccumulationChart } from '@syncfusion/ej2-charts';
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: undefined }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: null }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            emptyPointSettings: { mode: 'Average', fill: 'pink'}
            xName: 'x',
            yName: 'y'
        }
    ]
}, '#element');

```

{% endtab %}