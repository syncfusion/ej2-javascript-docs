---
title: " Chart Category Axis | TypeScript "

component: "Chart"

description: "Category axis are used to represent, the string values instead of numbers.It contains range, label placement customizations."
---

# Category Axis

<!-- markdownlint-disable MD036 -->

Category axis are used to represent, the string values instead of numbers.

{% tab template= "chart/axis", es5Template="es5AxisCategory" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { country: "USA", gold: 50 },
      { country: "China", gold: 40 },
      { country: "Japan", gold: 70 },
      { country: "Australia", gold: 60 },
      { country: "France", gold: 50 },
      { country: "Germany", gold: 40 },
      { country: "Italy", gold: 40 },
      { country: "Sweden", gold: 30 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        //Category in primary X Axis
        valueType: 'Category',
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

>Note: To use category axis, we need to inject `Category` module using `Chart.Inject(Category)` method and
set the [`valueType`](../api/chart/axis/) of axis to Category.

## Labels Placement

By default, category labels are placed between the ticks in an axis, this can also be placed on ticks
using [`labelPlacement`](../api/chart/axis/) property.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        // label placement as on ticks
        labelPlacement: 'OnTicks',
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Range

Range of the category axis can be customized using [`minimum`](../api/chart/axis/),
[`maximum`](../api/chart/axis/) and [`interval`](../api/chart/axis/) property of
the axis.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        interval: 2, minimum: 1, maximum: 5
    },
    series:[{
        dataSource: categoryData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Indexed category axis

Category axis also can be rendered based on the index values of data source. This can be achieved by defining the `isIndexed` property to `true` in the axis.

{% tab template= "chart/axis", es5Template="es5AxisPosition" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { categoryData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        isIndexed: true
    },
     //Initializing Chart Series
        series: [
            {
                type: 'Column',
                dataSource: [{ x: 'Myanmar', y: 7.3 }, { x: 'India', y: 7.9 }, { x: 'Bangladesh', y: 6.8 }, { x: 'Cambodia', y: 7.0 }, { x: 'China', y: 6.9 }],
                xName: 'x', yName: 'y',
            },
            {
                type: 'Column',
                dataSource: [{ x: 'Poland', y: 2.7 },{ x: 'Australia', y: 2.5 },{ x: 'Singapore', y: 2.0 },{ x: 'Canada', y: 1.4 },{ x: 'Germany', y: 1.8 }],
                xName: 'x',yName: 'y',
            }],

}, '#element');

```

{% endtab %}