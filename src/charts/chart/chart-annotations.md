---
title: " Chart Annotations | TypeScript "

component: "Chart"

description: "Chart annotations are used to mark the specific area of interest in the chart area with texts, shapes or images."
---

# Annotation

Annotations are used to mark the specific area of interest in the chart area with texts, shapes or images.

<!-- markdownlint-disable MD033 -->

You can add annotations to the chart by using the <code>annotations</code> option. By using the [`content`](../api/chart/chartAnnotationSettingsModel/#content-string)
option of annotation object, you can specify either the id of the element or directly specify the element in the content that needs to be displayed in the chart area.

{% tab template= "chart/chart-appearance", es5Template="es5Annotation" %}

```typescript

import { Chart, ColumnSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    annotations:[{
        content: '70 Gold Medals',
        coordinateUnits: 'Point',
        x: 'France',
        y: 50
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

>Note: To use annotations feature, we need to inject `ChartAnnotation` using `Chart.Inject(ChartAnnotation)` method.

## Region

Annotations can be placed either with respect to `Series` or `Chart`. by default, it will placed with respect to `Chart`.

{% tab template= "chart/chart-appearance", es5Template="es5Annotation" %}

```typescript

import { Chart, ColumnSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    annotations:[{
        content: '<div>Highest Medal Count</div>',
        region: 'Series',
        coordinateUnits: 'Point',
        x: 'France',
        y: 50
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Co-ordinate Units

Specified the coordinates units of the annotation either `Pixel` or `Point`.

 {% tab template= "chart/chart-appearance", es5Template="es5Annotation" %}

```typescript

import { Chart, ColumnSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    annotations:[{
        content: '<div style="border: 1px solid black; padidng: 5px 5px 5px 5px, backgrund:#f5f5f5">Annotation in Pixel</div>',
        coordinateUnits: 'Pixel',
        x: 150,
        y: 50
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Alignment

Annotation provides `verticalAlignment` and `horizontalAlignment`. The `verticalAlignment` can be customized via `Top`, `Bottom` or `Middle` and the `horizontalAlignment` can be customized via `Near`, `Far` or `Center`.

{% tab template= "chart/chart-appearance", es5Template="es5Annotation" %}

```typescript

import { Chart, ColumnSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    annotations:[{
        content: '<div style="border: 1px solid black; padidng: 5px 5px 5px 5px, backgrund:#f5f5f5">Highest Medal Count</div>',
        x: 'France',
        y: 50,
        verticalAlignment:'Top',
        horizontalAlignment:'Near'
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## Adding y-axis sub title through on annotation

By setting text div in the `content` option of annotation object you can add sub title to chart y-axis. Specified the
`coordinate` value as `pixel` and customize x and y location of the text.

{% tab template= "chart/chart-appearance", es5Template="es5Annotationsubtitle" %}

```typescript

import { Chart, ColumnSeries, Category, ChartAnnotation } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, ChartAnnotation);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
     primaryYAxis: {
      title: '(m2/min)'
    },
    annotations:[{
        content: '<div id="text" style="transform: rotate(-90deg);">Speed Rate</div>',
        x: 6,
        y: 180,
        coordinateUnits: 'Pixel',
        Region: 'Chart'
    }],
    series:[{
        dataSource: columnData,
        xName: 'country', yName: 'gold',
        type: 'Column'
    }],

}, '#element');

```

{% endtab %}

## See Also

* [Show total stacking values in data label](../chart/how-to/stacking-total/#show-the-total-value-for-stacking-series-in-data-label)
* [Create footer and watermark for chart](../chart/how-to/footer/#create-footer-and-watermark-for-chart)
