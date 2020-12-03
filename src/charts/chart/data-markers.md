---
title: " Chart Marker | TypeScript "

component: "Chart"

description: "Data markers are used to provide information about the data points in the series. You can add a shape to adorn each data point."
---

# Data Markers

Data markers are used to provide information about the data points in the series. You can add a shape to adorn each data point.

<!-- markdownlint-disable MD036 -->

## Marker

<!-- markdownlint-disable MD036 -->

Markers can be added to the points by enabling the [`visible`](../api/chart/markerSettingsModel/#visible-boolean) option of the marker property.

{% tab template= "chart/data-markers", es5Template="es5DefultMarker" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                }
            }
        ],

}, '#element');

```

{% endtab %}

## Shape

Markers can be assigned with different shapes such as Rectangle, Circle, Diamond etc using the `shape`property.

{% tab template= "chart/data-markers", es5Template="es5DefultMarker" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    shape:'Diamond',
                    height: 10, width: 10
                }
            }
        ],
}, '#element');

```

{% endtab %}

>Note : To know more about the marker shape type refer the [`shape`](../api/chart/markerSettings/#shape-string).

## Images

Apart from the shapes, you can also add custom images to mark the data point using the [`imageUrl`](../api/chart/markerSettingsModel/#imageurl-string) property.

{% tab template= "chart/data-markers", es5Template="es5ImageMarker" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, Category);

let chart: Chart = new Chart({
         series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                //Marker shape as image
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Image',
                    imageUrl:'sun_annotation.png'
                }
            }
        ],

}, '#element');

```

{% endtab %}

## Customization

Marker's color and border can be customized using `fill` and `border` properties.

{% tab template= "chart/data-markers", es5Template="es5DefultMarker" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, Category);

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    fill: 'Red', height: 10, width: 10,
                    border:{width: 2, color: 'blue'},
                }
            }
        ],

}, '#element');

```

{% endtab %}

## Customizing Specific Point

You can also customize the specific marker and label using [`pointRender`](../api/chart/#pointrender-emittypeipointrendereventargs) event. `pointRender` event allows
you to change the shape, color and border for a point.

{% tab template= "chart/data-markers", es5Template="es5Point" %}

```typescript

import { Chart, LineSeries, IPointRenderEventArgs } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries);

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    height: 10, width: 10,
                }
            }
        ],
       // pointRender event for chart
        pointRender: (args: IPointRenderEventArgs) => {
            if(args.point.index === 3){
                args.fill = 'red'
            }
        },
}, '#element');

```

{% endtab %}

## See Also

* [Customize the marker with different shape](./how-to/marker-customization#customize-the-marker-with-different-shape)