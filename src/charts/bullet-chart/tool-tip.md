---
title: "BulletChart Tooltip | TypeScript "

component: "BulletChart"

description: "Tooltip is used to show the data value when mouse hover on the chart.We can able to customize format,template and appearance."
---

# Tooltip

<!-- markdownlint-disable MD036 -->

'Bullet Chart' will display the details of 'Actual' and 'Target' values through 'Tooltip' when the mouse is moved over the 'Target' and the 'Feature' bar.

## Default Tooltip

By setting [`enable`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#enable)the property to 'True' and by injecting `BulletTooltip` module
using `BulletChart.Inject(BulletTooltip)`.The 'Tooltip' is visible in the 'Bullet chart' by default.

{% tab template= "bullet-chart/user-interaction", es5Template="es5Tooltip" %}

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
        minimum: 0, maximum: 100, interval: 20,
        tooltip: { enable: true }
}, '#element');

```

{% endtab %}

## Tooltip Template

Any 'HTML' elements can be displayed in the 'Tooltip' by using the 'Tooltip' property `Template.` You can use the ${target} and ${value} as place holders in the 'HTML' element to display the 'Value' and 'Target' values of the corresponding data point.

{% tab template= "bullet-chart/user-interaction", es5Template="es5TooltipTemplate" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        height: '110px',
        tooltip: { enable: true, template : '#Tooltip' },
        dataSource: [{ value: 70, target: 50 }],
        valueField: 'value',
        targetField: 'target',
        animation: { enable: false },
        ranges: [{ end: 30, color: '#599C20' },
        { end: 60, color: '#EFC820' },
        { end: 100, color: '#CA4218' }
        ],
        minimum: 0, maximum: 100, interval: 10,
        title: 'Revenue YTD',
        labelFormat: '${value}K'
}, '#element');

```

{% endtab %}

## Customization of the appearance of 'Tooltip'

The [`fill`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#fill) and [`border`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#border) properties are used to customize the background color and border of the tooltip respectively. The [`textStyle`](https://ej2.syncfusion.com/documentation/api/bullet-chart/bulletTooltipSettingsModel/#textstyle) property in the tooltip is used to customize the font of the tooltip text.

{% tab template= "chart/user-interaction", es5Template="es5Appearance" %}

```typescript

import { BulletChart, BulletTooltip } from '@syncfusion/ej2-charts';
BulletChart.Inject(BulletTooltip);

let chart: BulletChart = new BulletChart({
        height: '110px',
        tooltip: { enable: true, fill: 'red', border:{ color: 'green', width: 10 } },
        dataSource: [{ value: 70, target: 50 }],
        valueField: 'value',
        targetField: 'target',
        animation: { enable: false },
        ranges: [{ end: 30, color: '#599C20' },
        { end: 60, color: '#EFC820' },
        { end: 100, color: '#CA4218' }
        ],
        minimum: 0, maximum: 100, interval: 10,
        title: 'Revenue YTD',
        labelFormat: '${value}K'
}, '#element');

```

{% endtab %}