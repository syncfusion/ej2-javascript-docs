---
title: " Bullet Chart DataBinding | TypeScript "

component: "Bullet Chart"

description: "Bullet Chart can be rendered by using different types of data source. They are called local data, remote data. "
---
<!-- markdownlint-disable MD036 -->

# Working with Data

Bullet Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/bullet-chart/) direct property of the bullet-chart. Now map the fields in
JSON to [`valueField`](../api/bullet-chart/#valueField-string) and [`targetField`](../api/bullet-chart/#targetField-string) properties.

{% tab template= "bullet-chart/dataSource", es5Template="es5LocalData" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let localData: any[] = [
        {
            value: 5, comparativeMeasureValue: 7.5,
            category: '2001'
        },
        {
            value: 7, comparativeMeasureValue: 5,
            category: '2002'
        },
        {
            value: 10, comparativeMeasureValue: 6,
            category: '2003'
        },
        {
            value: 5, comparativeMeasureValue: 8,
            category: '2004'
        },
        {
            value: 12, comparativeMeasureValue: 5,
            category: '2005'
        },
        {
            value: 8, comparativeMeasureValue: 6,
            category: '2006'
        }
];

let chart: BulletChart = new BulletChart({
       dataSource: localData,
        animation: { enable: false },
        valueField: 'value',
        targetField: 'comparativeMeasureValue',
        title: 'Profit in %',
        height: '400',
        ranges: [{ end: 5 },
            { end: 15 },
            { end: 20 }
        ],
        minimum: 0, maximum: 20, interval: 5,
}, '#element');

```

{% endtab %}