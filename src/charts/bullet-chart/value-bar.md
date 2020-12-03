---
title: " Bullet Chart Value Bar | TypeScript "

component: "Bullet Chart"

description: "The main data value is encoded by a length of the main bar in the middle of the chart, known as the Feature Measure. "
---
<!-- markdownlint-disable MD036 -->

# Feature Bar

The main data value is encoded by a length of the main bar in the middle of the chart, known as the `Feature Measure`. This is also called as `value Bar`. Also, if you want to display the target bar you should map the `valueField` name from the dataSource.

{% tab template= "bullet-chart/featurebar", es5Template="es5ValueBar" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
      title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        valueField: 'value',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

## Feature bar types

You can customize the shape of the feature bar or value bar using the `type` property of the bullet chart. Feature bar contains `Rect` and `Dot` shapes. The default type of feature bar is `Rect`.

{% tab template= "bullet-chart/featurebar", es5Template="es5ValueType" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        valueField: 'value',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        type: 'Dot',
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

## Customization

**Border customization**

Using the `valueBorder` property of the bullet chart, you can customize the border `color` and `width` of the feature bar.

{% tab template= "bullet-chart/featurebar", es5Template="es5ValueBorder" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
       title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        valueField: 'value',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        valueBorder: { color: 'red', width: 3 },
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}

**Fill color and height customization**

You can customize the fill color and height of the feature bar using the `valueFill` and `valueHeight` properties of the bullet chart.

{% tab template= "bullet-chart/featurebar", es5Template="es5valueFill" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
       title: 'Sales Rate',
        dataSource: [
        { value: 55, target: 75, category: 'Year 1'  },
        ],
        animation: { enable: false },
        valueField: 'value',
        ranges: [ { end: 35 },
        { end: 50 },
        { end: 100 }
        ],
        valueFill: 'blue',
        valueHeight: 15,
        minimum: 0, maximum: 100, interval: 20
}, '#element');

```

{% endtab %}