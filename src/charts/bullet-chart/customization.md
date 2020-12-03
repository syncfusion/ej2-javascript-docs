---
title: " Bullet Chart Customization | TypeScript "

component: "Bullet Chart"

description: "Bullet Chart have different customizable features like different orientation, flow directions and animation features"
---
<!-- markdownlint-disable MD036 -->

# Orientation

Bullet Chart can be rendered in different mode as `Horizontal` or `vertical` by using `orientation` property of the bullet-chart. By default bullet-chart rendered in horizontal mode.

{% tab template= "bullet-chart/customize", es5Template="es5Orientation" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        title: 'Sales Rate in dollars',
        subtitle: '(in dollars $)',
        dataSource: [
        { value: 55, target: 45, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        valueField: 'value',
        labelFormat: '${value}',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        width: '20%',
        orientation: 'Vertical',
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

## Flow Direction

Using `enableRtl` boolean property of the bullet-chart, you can render bullet-chart in right to left or left to right direction.

{% tab template= "bullet-chart/customize", es5Template="es5Flow" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        dataSource: [
        { value: 1500, target: 1000, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        valueField: 'value',
        ranges: [{ end: 500 },
        { end: 1500 },
        { end: 2000 }
        ],
        enableRtl: true,
        minimum: 0, maximum: 2000, interval: 200
}, '#element');

```

{% endtab %}

## Animation

By setting `animation` property value as `true`, you can enable the linear animation of the feature and target bars.

{% tab template= "bullet-chart/customize", es5Template="es5animation" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        dataSource: [
        { value: 1500, target: 1000, category: 'Year 1'  },
        ],
        animation: { enable: true },
        targetField: 'target',
        valueField: 'value',
        ranges: [ { end: 500 },
        { end: 1500 },
        { end: 2000 }
        ],
        minimum: 0, maximum: 2000, interval: 200
}, '#element');

```

{% endtab %}

## Theme

Bullet chart also support different types of themes. Using `theme` property of the bullet-chart, you can customize the theme styles.

{% tab template= "bullet-chart/customize", es5Template="es5theme" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        title: 'Profit in %',
        dataSource: [
        { value: 50, target: 45, category: 'Year 1'  },
        ],
        animation: { enable: false },
        targetField: 'target',
        valueField: 'value',
        ranges: [ { end: 15 },
        { end: 50 },
        { end: 100 }
        ],
        theme: 'HighContrast',
        minimum: 0, maximum: 100, interval: 10
}, '#element');

```

{% endtab %}