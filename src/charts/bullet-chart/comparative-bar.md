---
title: " Bullet Chart Target Bar | TypeScript "

component: "Bullet Chart"

description: "The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure`. "
---
<!-- markdownlint-disable MD036 -->

# Target Bar

The line marker that runs perpendicular to the orientation of the graph is known as the `Comparative Measure` and is used as a target marker to compare against the Feature Measure value. This is also called as `Target Bar` of the bullet chart. Also, if you want to display the target bar you should map the `targetField` name from the dataSource.

{% tab template= "bullet-chart/targetbar", es5Template="es5TargetBar" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

## Target Bar Types

You can customize the shape of the target bar or comparative bar using the `targetTypes` property of the bullet chart. Target bar contains `Circle`, `Cross`, and `Rect` shapes. The default type of target bar is `Rect`.

{% tab template= "bullet-chart/targetbar", es5Template="es5TargetTypes" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        targetTypes: ['Circle'],
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

## Customization

**Color Customization**

Using the `targetColor` property of the bullet chart, you can customize the fill color of the target bar.

{% tab template= "bullet-chart/targetbar", es5Template="es5targetColor" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
     title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        targetColor: 'red',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

**Width Customization**

You can customize the width of the target bar using the `targetWidth` property of the bullet chart.

{% tab template= "bullet-chart/targetbar", es5Template="es5TargetWidth" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
       title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        targetWidth: 15,
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}