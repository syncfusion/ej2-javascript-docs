---
title: " Bullet Chart Appearance | TypeScript "

component: "Bullet Chart"

description: "We can set bullet-chart size manually by using width and height properties. We can set percentage or pixel size values to the bullet-chart."
---

# Bullet Chart Dimensions

## Size for container

The bullet chart can be rendered to its container’s size. You can set the size using inline or CSS as shown below.

```javascript
    <div id='container'>
        <div id='element' style="width:650px; height:350px;"></div>
    </div>
```

{% tab template= "bullet-chart/bullet-chart-dimensions", es5="es5Dimensions" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        width: '650px',
        height: '350px',
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5,
}, '#element');

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Size for Bullet Chart

<!-- markdownlint-disable MD036 -->

You can also set the size for bullet chart directly using the [`width`](../api/bullet-chart/#width-string) and [`height`](../api/bullet-chart/#height-string) properties.

**In Pixel**

You can set the size of a chart in pixels as shown below.

{% tab template= "bullet-chart/bullet-chart-dimensions", es5Template="es5bulletchartSize" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
       //width and height for chart in pixel
        width: '650', height: '350',
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5,
}, '#element');

```

{% endtab %}

**In Percentage**

By setting a value in percentage, the bullet chart gets its dimension with respect to its container. For example, when the height is ‘50%’, the bullet chart renders to half of the container’s height.

{% tab template= "bullet-chart/bullet-chart-dimensions", es5Template="es5BulletChartSizePercent" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        // Width and height for chart in percentage
        width: '80%', height: '90%',
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5,
}, '#element');

```

{% endtab %}

>Note: When you do not specify the size, it takes `126px` as its height and window size as its width.