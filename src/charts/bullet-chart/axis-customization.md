---
title: " Bullet Chart Axis Customization | TypeScript "

component: "Bullet Chart"

description: "Bullet Chart axis contains different customization like majortick and minortick, axis label, axis range customizations"
---

# Axis Customization

## MajorTickLines and MinorTickLines Customization

You can customize the `width`, `color`, and `size` of minor and major tick lines using the
[`majorTickLines`](../api/bullet-chart/bulletChartModel/) and
[`minorTickLines`](../api/bullet-chart/bulletChartModel/) properties of the bullet-chart.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5TickCustom" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        //color and width customization of the major and minor ticks
        majorTickLines: { color: 'blue', width: 5 },
        minorTickLines: {width: 4, color: 'red'},
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5
}, '#element');

```

{% endtab %}

## Tick Placement

You can place major and minor ticks `inside` or `outside` the ranges using the [`tickPosition`](../api/bullet-chart/bulletChartModel/) property of bullet-chart.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5TickPlacement" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        // To place the ticks inside of the bullet-chart
        tickPosition: 'Inside',
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5
}, '#element');

```

{% endtab %}

## Label Format

***Axis Label Format***

Axis numeric labels can be formatted by using the [`labelFormat`](../api/bullet-chart/bulletChartModel/#labelformat)property. Axis labels support all globalize formats. The following table describes the result of applying some commonly used label formats on numeric axis values.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5LabelFormat" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        //Label format as currency
        labelFormat: 'c',
        title: 'Sales Rate',
        dataSource: [{ value: 1500, target: 1300 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 500 },
            { end: 1500 },
            { end: 2500 }
        ],
        minimum: 0, maximum: 2500, interval: 250
}, '#element');

```

{% endtab %}

The following 'Table' describes the result of applying some commonly used 'Label' formats on Numeric axis values.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

## GroupingSeparator

To separate groups of thousands, use the [`enableGroupSeparator`](../api/bullet-chart/bulletChartModel/#enablegroupseparator) property of bullet-chart.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5GroupingSep" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        enableGroupSeparator: true,
        title: 'Sales Rate',
        dataSource: [{ value: 1500, target: 1300 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 500 },
            { end: 1500 },
            { end: 2500 }
        ],
        minimum: 0, maximum: 2500, interval: 250
}, '#element');

```

{% endtab %}

## Custom Label Format

You can also customize the axis label format using a placeholder like ${value}K, in which the value represents the axis label, e.g. $20K.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5CustomFormat" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        labelFormat: '${value}K',
        title: 'Sales Rate',
        dataSource: [{ value: 1500, target: 1300, category: 'Product A'  }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 500 },
            { end: 1500 },
            { end: 2500 }
        ],
        minimum: 0, maximum: 2500, interval: 250
}, '#element');

```

{% endtab %}

## Label Placement

You can customize the axis labels `inside` or `outside` the bullet-chart using the [`labelPosition`](../api/bullet-chart/bulletChartModel/#labelposition) property .

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5labelPlacement" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        // To place the axis label inside of the bullet-chart
        labelPosition: 'Inside',
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, interval: 5
}, '#element');

```

{% endtab %}

## Opposed Position

To place an axis opposite to its original position,
set the [`opposedPosition`](../api/bullet-chart/bulletChartModel/#opposedposition) property to true.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5Opposed" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        opposedPosition: true,
        dataSource: [{ value: 23, target: 22 }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        ranges: [{ end: 20 },
            { end: 25 },
            { end: 30 }
        ],
        minimum: 0, maximum: 30, interval: 5
}, '#element');

```

{% endtab %}

## Category Label

You can display the x axis label by mapping the `categoryField` from dataSource of a bullet-chart. It is a more efficient way to understand data.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5Category" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
        title: 'Sales Rate',
        dataSource: [{ value: 1500, target: 1300, category: 'Product A'  }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        categoryField: 'category',
        ranges: [{ end: 500 },
            { end: 1500 },
            { end: 2500 }
        ],
        minimum: 0, maximum: 2500, interval: 250
}, '#element');

```

{% endtab %}

## Category Label Customization

You can customize the category label by using the `categoryLabelStyle` property of the bullet-chart.

{% tab template= "bullet-chart/bullet-chart-axis", es5Template="es5CategoryStyle" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);
let chart: BulletChart = new BulletChart({
       title: 'Sales Rate',
        dataSource: [{ value: 1500, target: 1300, category: 'Product A'  }],
        animation: { enable: false },
        valueField: 'value',
        targetField: 'target',
        categoryField: 'category',
        categoryLabelStyle: { color: 'Orange'},
        ranges: [{ end: 500 },
            { end: 1500 },
            { end: 2500 }
        ],
        minimum: 0, maximum: 2500, interval: 250
}, '#element');

```

{% endtab %}