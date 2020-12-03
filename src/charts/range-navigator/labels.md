---
title: " RangeNavigator Labels | TypeScript "

component: "RangeNavigator"

description: "RangeNavigator supports Multilevel label and enable grouping properties to customize axis labels."
---

# Labels

## Multilevel labels

The second level labels for the range navigator can be enabled by setting the “enableGrouping” property to true.
This is restricted to date-time axis alone.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, DateTime, RangeTooltip } from '@syncfusion/ej2-charts';
RangeNavigator.Inject( DateTime, RangeTooltip);

let data: object[] = [];
let value: number = 0; let point: object = {};
for (let j: number = 1; j < 1090; j++) {
    value += (Math.random() * 10 - 5);
    value = value < 0 ? Math.abs(value) : value;
    point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
    data.push(point);
}
let range: RangeNavigator = new RangeNavigator(
        {
            labelPosition: 'Outside',
            tooltip: { enable: true },
            valueType: 'DateTime',
            intervalType: 'Quarter',
            enableGrouping: true,
            value: [new Date(2001, 0), new Date(2002, 0)],
            dataSource: data,
            xName: 'x',
            yName: 'y'
        }, '#element');

```

{% endtab %}

## Grouping

The second level axis labels can be grouped using “groupBy” property with the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, DateTime, RangeTooltip } from '@syncfusion/ej2-charts';
RangeNavigator.Inject( DateTime, RangeTooltip);

let data: object[] = [];
let value: number = 0; let point: object = {};
for (let j: number = 1; j < 1090; j++) {
    value += (Math.random() * 10 - 5);
    value = value < 0 ? Math.abs(value) : value;
    point = { x: new Date(2000, 0, j), y: value, z: value + 10 };
    data.push(point);
}
let range: RangeNavigator = new RangeNavigator(
        {
            labelPosition: 'Outside',
            tooltip: { enable: true },
            valueType: 'DateTime',
            intervalType: 'Quarter',
            enableGrouping: true,
            groupBy: 'Years',
            value: [new Date(2001, 0), new Date(2002, 0)],
            dataSource: data,
            xName: 'x',
            yName: 'y'
        }, '#element');

```

{% endtab %}

## Smart labels

The “labelIntersectAction” property is used to avoid overlapping of labels.

The following code sample shows setting the labelIntersectAction property to Hide.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    labelIntersectAction: 'Hide',
    labelFormat:'y/M/d',
    value:[new Date("2017-08-13"), new Date("2017-12-28")],
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Label positioning

By default, the labels can be placed at outside of the range navigator. You can place the labels inside the range navigator
using the labelPosition property.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    labelPosition: 'Inside',
    value:[new Date("2017-08-13"), new Date("2017-12-28")],
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Labels customization

The font size, color, family, etc. can be customized using the “labelStyle” property.

{% tab template= "rangenavigator/lightweight", es5Template="es5LW" %}

```typescript

import { RangeNavigator, DateTime } from '@syncfusion/ej2-charts';
import { GetDateTimeData } from './datasource.ts';
RangeNavigator.Inject(DateTime);

let range: RangeNavigator = new RangeNavigator(
        {
            valueType: 'DateTime',
            intervalType: 'Months',
            labelFormat: 'MMM',
            labelStyle: { color: 'red', size:'10px'}
            value: [new Date(2018, 5, 1), new Date(2018, 6, 1)],
            dataSource: GetDateTimeData(new Date(2018, 0, 1), new Date(2019, 0, 1)),
            xName: 'x', yName: 'y'
        }, '#element');
```

{% endtab %}
