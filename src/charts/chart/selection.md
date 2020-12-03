---
title: " Chart Selection | TypeScript "

component: "Chart"

description: "Strip Lines are vertical or horizontal lines used to highlight/mark a certain region on the plot area."
---
<!-- markdownlint-disable MD036 -->

# Selection

Chart provides selection support for the series and its data points on mouse click.

>When Mouse is clicked on the data points, the corresponding series legend also will be selected.

We have different types of selection mode for selecting a data.

* None
* Point
* Series
* Cluster
* DragXY
* DragX
* DragY

## Point

You can select a point, by setting `selectionMode` to point.

{% tab template= "chart/user-interaction", es5Template="es5PointSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);

let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    // selection mode as point
    selectionMode: 'Point',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Series

You can select a series, by setting `selectionMode` to series.

{% tab template= "chart/user-interaction", es5Template="es5SeriesSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData ,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    // selection mode as series
    selectionMode: 'Series',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Cluster

You can select the points that corresponds to the same index in all the series, by setting `selectionMode` to cluster.

{% tab template= "chart/user-interaction", es5Template="es5ClusterSelect" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData ,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    // selection mode as cluster
    selectionMode: 'Cluster',
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Rectangular selection

**DragXY, DragX and DragY**

To fetch a collection of data under a particular region, you have to set `selectionMode` as `DragXY`.

* DragXY - Allow us to select data with respect to both horizontal and vertical axis.
* DragX - Allow us to select data with respect to horizontal axis.
* DragY - Allow us to select data with respect to vertical axis.

The selected data’s are returned as an array collection in the
[`dragComplete`](../api/chart/#dragcomplete-emittypeidragcompleteeventargs) event.

{% tab template= "chart/user-interaction", es5Template="es5DragSelect" %}

```typescript

import { Chart, ScatterSeries, Legend, Selection } from '@syncfusion/ej2-charts';
import { rectData } from './datasource.ts';
Chart.Inject(ScatterSeries, Legend, Selection);

let chart: Chart = new Chart({
    series: [
            {
                type: 'Scatter',
                dataSource: rectData ,
                xName: 'x',
                yName: 'y', name: 'Product A',
                marker: {
                    shape: 'Triangle',
                    width: 10, height: 10
                }
            },
    ]
    // selection mode as dragxy
    selectionMode: 'DragXY',
    title: 'Height Vs Weight'
}, '#element');

```

{% endtab %}

## Selection type

You can select multiple points or series, by enabling the [`isMultiSelect`](../api/chart/#ismultiselect-boolean)
property.

{% tab template= "chart/user-interaction", es5Template="es5SelectionType" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData ,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    selectionMode: 'Series',
    // multipselect forselection
    isMultiSelect: true,
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Selection on load

You can able to select a point or series programmatically on a chart using
[`selectedDataIndexes`](../api/chart/#selecteddataindexes-indexesmodel) property.

{% tab template= "chart/user-interaction", es5Template="es5Load" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts'
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData ,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection1'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection2'
    }, {
        dataSource: selectionData ,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        animation: {enable: false},
        selectionStyle: 'chartSelection3'
    }],
    selectionMode: 'Point',
    isMultiSelect: true,
    // Selcted data indexes for chart series
    selectedDataIndexes: [
        { series: 0, point: 1}, { series: 2, point: 3}
    ],
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Selection through on legend

You can able to select a point or series through on legend using
[`toggleVisibility`](../api/chart/legendSettingsModel/#toggleVisibility-toggleVisibility) property.

{% tab template= "chart/user-interaction", es5Template="es5Load" %}

```typescript
import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts'
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column',
        animation: {enable: false},
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        animation: {enable: false},
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        animation: {enable: false},
    }],
    selectionMode: 'Point',
    // Selection through on legend
    legendSettings: { visible: true, toggleVisibility: false }
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## Customization for selection

You can apply custom style to selected points or series with [`selectionStyle`](../api/chart/series/#selectionstyle-string) property.

{% tab template= "chart/user-interaction", es5Template="es5SelectionStyle" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
import { selectionData } from './datasource.ts'
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    series:[{
        dataSource: selectionData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column',
        //Selection style for chart series selection
        selectionStyle: 'chartSelection1'
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        selectionStyle: 'chartSelection2'
    }, {
        dataSource: selectionData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        selectionStyle: 'chartSelection3'
    }],
    selectionMode: 'Point',
    isMultiSelect: true,
    title: 'Olympic Medals'
}, '#element');

```

{% endtab %}

## See Also

* [Display selected data for range selection](./how-to/#display-selected-data-for-range-selection)
