---
title: " Accumulation Chart Annotation | TypeScript "

component: "Accumulation Chart"

description: "The annotations are used to mark the specific area of interest in the chart area with texts, shapes or images."
---

# Annotation

The annotations are used to mark the specific area of interest in the chart area with texts, shapes or images.

<!-- markdownlint-disable MD033 -->

By using the <code>content</code> option of annotation property, you can specify the Id of the element that needs to be displayed in the chart area

{% tab template="chart/chart-types", es5Template="es5AccAnnotation" %}

```typescript

import { AccumulationChart, AccumulationAnnotation } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationAnnotation);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 13, text: 'Jan: 13' }, { x: 'Feb', y: 13, text: 'Feb: 13' },
                        { x: 'Mar', y: 17, text: 'Mar: 17' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' }],
            xName: 'x',
            yName: 'y'
        }
    ],
    annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 13
    }],

}, '#element');

```

{% endtab %}

>Note: To use the annotations feature, inject the `AccumulationAnnotation` using the

`Chart.Inject(AccumulationAnnotation)` method.

## Region

The annotation can be placed with respect to either `Series` or `Chart`.

{% tab template="chart/chart-types", es5Template="es5AccAnnotation" %}

```typescript

import { AccumulationChart, AccumulationAnnotation } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationAnnotation);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }
    ],
    annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">13.5</div>',
        region: 'Chart',
        coordinateUnits: 'Pixel',
        x: 150,
        y: 150
    }],

}, '#element');

```

{% endtab %}

## Co-ordinate Units

Specifies the coordinate units of an annotation either in `Pixel` or `Point`.

{% tab template="chart/chart-types", es5Template="es5AccAnnotation" %}

```typescript

import { AccumulationChart, AccumulationAnnotation } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationAnnotation);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }
    ],
    annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">Jan : 13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 13
    }],

}, '#element');

```

{% endtab %}

## Alignment

The annotations can be moved vertically and horizontally from its default position by using `verticalAlignment`
or `horizontalAlignment` properties. The verticalAlignment property takes value as `Top`, `Bottom` or `Middle` and the
horizontalAlignment property takes value as `Near`, `Far` or `Center`.

{% tab template="chart/chart-types", es5Template="es5AccAnnotation" %}

```typescript

import { AccumulationChart, AccumulationAnnotation } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationAnnotation);
let piechart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }
    ],
    annotations:[{
        content:'<div style="border: 1px solid black;background-color:#f5f5f5; padding: 5px 5px 5px 5px">Jan : 13.5</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'Jan',
        y: 13,
        verticalAlignment:'Top',
        horizontalAlignment:'Near'
    }],

}, '#element');

```

{% endtab %}