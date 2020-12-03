---
title: "Accumulation Chart Grouping | TypeScript "

component: "Accumulation Chart"

description: "By using point and value in pie chart,you can group collection of points into the single slice"
---

# Grouping

You can club/group few points of the series based on
[`groupTo`](../api/accumulation-chart/accumulationSeries/) property. For example, if the club
value is 11, then the points with value less than 11 is grouped together and will be showed as a single
point with label `others`. The property also takes value in percentage (percentage of total data points value).

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, AccumulationDataLabel, IAccTextRenderEventArgs, IAccPointRenderEventArgs } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationDataLabel);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [
                { x: 'Jan', y: 3, text: 'Jan: 3' }, { x: 'Feb', y: 3.5, text: 'Feb: 3.5' },
                { x: 'Mar', y: 7, text: 'Mar: 7' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' },
                { x: 'May', y: 19, text: 'May: 19' }, { x: 'Jun', y: 23.5, text: 'Jun: 23.5' },
                { x: 'Jul', y: 26, text: 'Jul: 26' }, { x: 'Aug', y: 25, text: 'Aug: 25' },
                { x: 'Sep', y: 21, text: 'Sep: 21' }, { x: 'Oct', y: 15, text: 'Oct: 15' },
                { x: 'Nov', y: 9, text: 'Nov: 9' }, { x: 'Dec', y: 3.5, text: 'Dec: 3.5' }],
            dataLabel: { visible: true, name: 'text', position: 'Outside'  },
            groupTo: '11',
            xName: 'x',
            yName: 'y'
        }
    ],

}, '#element');

```

{% endtab %}

## Group Mode

Slice can also be grouped based on number of points by specifying the `groupMode` to Point. For example, if the group to value is 11, accumulation chart will show 1st 11 points and will group remaining entries in the collection as a single point.

{% tab template="chart/chart-types", es5Template="es5AccGroupMode" %}

```typescript

import { AccumulationChart, AccumulationDataLabel, IAccTextRenderEventArgs } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);
let accChart: AccumulationChart = new AccumulationChart({
   series: [
        {
            dataSource: data,
            dataLabel: { visible: true, position: 'Outside' },
            groupTo: '4',
            groupMode : 'Point',
            xName: 'x',
            yName: 'y'
        }
    ],

     textRender: (args: IAccTextRenderEventArgs) => {
        if (args.text.indexOf('Others') > -1) {
            args.text = 'Grouped Slices';
            args.color = 'red';
            args.border.width = 1;
        }
    },
    pointRender: (args: IAccPointRenderEventArgs) => {
        if ((args.point.x as string).indexOf('Others') > -1) {
            args.fill = '#D3D3D3';
        }
    },
}, '#element');

```

{% endtab %}

## Customization

You can customize the grouped point and its data label using `pointRender` and `textRender` event.

{% tab template="chart/chart-types", es5Template="es5AccGroupTo" %}

```typescript

import { AccumulationChart, AccumulationDataLabel, IAccTextRenderEventArgs } from '@syncfusion/ej2-charts';
import { data } from './datasource.ts';
AccumulationChart.Inject(AccumulationDataLabel);
let accChart: AccumulationChart = new AccumulationChart({
   series: [
        {
            dataSource: data,
            dataLabel: { visible: true, position: 'Outside' },
            groupTo: '11',
            xName: 'x',
            yName: 'y'
        }
    ],

     textRender: (args: IAccTextRenderEventArgs) => {
        if (args.text.indexOf('Others') > -1) {
            args.text = 'Grouped Slices';
            args.color = 'red';
            args.border.width = 1;
        }
    },
    pointRender: (args: IAccPointRenderEventArgs) => {
        if ((args.point.x as string).indexOf('Others') > -1) {
            args.fill = '#D3D3D3';
        }
    },
}, '#element');

```

{% endtab %}
