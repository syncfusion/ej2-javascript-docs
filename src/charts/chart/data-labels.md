---
title: " Chart DataLabel | TypeScript "

component: "Chart"

description: "Data labels are names of the data points that are displayed on the x-axis of a chart and also used to highlight important data points"
---

# Data Labels

Data label can be added to a chart series by enabling the [`visible`](../api/chart/dataLabelSettingsModel/#visible-boolean) option in the dataLabel. By default, the labels will arrange smartly without overlapping.

{% tab template= "chart/data-markers", es5Template="es5DataLabels" %}

```typescript

import { Chart, ColumnSeries,Category, DataLabel } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries,Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        series: [
            {
                type: 'Column',
                dataSource: columnData, xName: 'country', yName: 'gold',
                marker: {
                    //Data label for chart series
                    dataLabel: { visible: true }
                }
            }
        ],

}, '#element');

```

{% endtab %}

>Note: To use data label feature, we need to inject `DataLabel` using `Chart.Inject(DataLabel)` method.

## Position

Using [`position`](../api/chart/dataLabelSettingsModel/#position-string) property, you can place the label
either on `Top`, `Middle`,`Bottom` or `Outer` (outer is applicable for column and bar type series).

{% tab template= "chart/data-markers", es5Template="es5MarkerPosition" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        primaryYAxis:
        {
            labelFormat: '{value}°C'
        },
        series: [
            {
                type: 'Column',
                dataSource: columnData, xName: 'country', yName: 'gold',
                marker: {
                    //Data label position as middle
                    dataLabel: { visible: true, position: 'Middle' }
                }
            }
        ],

}, '#element');

```

{% endtab %}

>Note: The position `Outer` is applicable for column and bar type series.

## DataLabel Template

Label content can be formatted by using the template option. Inside the template, you can add the placeholder text `${point.x}` and `${point.y}` to display corresponding data points x & y value.
Using [`template`](../api/chart/dataLabelSettingsModel/#template-string) property, you can set data label template in chart.

{% tab template= "chart/data-markers", es5Template="es5DataLabelTemplate" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        series: [
            {
                type: 'Column',
                dataSource: columnData, xName: 'country', yName: 'gold',
                marker: {
                    dataLabel: { visible: true, template:'<div style="background:#f5f5f5; border: 1px solid black; padding: 3px 3px 3px 3px"><div>${point.x}</div><div>${point.y}</div></div>' }
                }
            }
        ],

}, '#element');

```

{% endtab %}

## Text Mapping

Text from the data source can be mapped using `name` property.

{% tab template= "chart/data-markers", es5Template="es5MarkerPosition" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        series: [
            {
                type: 'Column',
                dataSource: [{ x: 'Jan', y: 12, text: 'January : 12°C' }, { x: 'Feb', y: 8, text: 'February : 8°C' }, { x: 'Mar', y: 11, text: 'March : 11°C' }, { x: 'Apr', y: 6, text: 'April : 6°C' }],
                xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    dataLabel: { visible: true,name: 'text' }
                }
            }
        ],
}, '#element');

```

{% endtab %}

## Margin

`margin` for data label can be applied to using `left`, `right`, `bottom` and `top` properties.

{% tab template= "chart/data-markers", es5Template="es5DataLabelTemplate" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        series: [
            {
                type: 'Column',
                dataSource: columnData, xName: 'country', yName: 'gold',
                marker: {
                    dataLabel: { visible: true,
                        border:{width: 1, color : 'red'},
                        margin:{
                            left:5,
                            right:5,
                            top:5,
                            bottom:5
                        }
                    }
                }
            }
        ],

}, '#element');

```

{% endtab %}

## Customization

`stroke` and `border` of data label can be customized using `fill` and `border` properties. Rounded corners can be customized using `rx` and `ry` properties.

{% tab template= "chart/data-markers", es5Template="es5DataLabelTemplate" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel } from '@syncfusion/ej2-charts';
import { columnData } from './datasource.ts';
Chart.Inject(ColumnSeries, Category, DataLabel);

let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category'
        },
        series: [
            {
                type: 'Column',
                dataSource: columnData, xName: 'country', yName: 'gold',
                marker: {
                    dataLabel: { visible: true,
                        border:{width: 2, color : 'red'},
                        rx:10, ry: 10
                    }
                }
            }
        ],

}, '#element');

```

{% endtab %}

>Note: `rx` and `ry` properties requires `border` values not to be null.

## Customizing Specific Point

You can also customize the specific marker and label using [`pointRender`](../api/chart/#pointrender-emittypeipointrendereventargs) and [`textRender`](../api/chart/#textrender-emittypeitextrendereventargs)  event. `pointRender` event allows
you to change the shape, color and border for a point, whereas the `textRender` event allows you to change the text for the point.

{% tab template= "chart/data-markers", es5Template="es5Point" %}

```typescript

import { Chart, LineSeries, DataLabel, IPointRenderEventArgs, ITextRenderEventArgs } from '@syncfusion/ej2-charts';
import { numData } from './datasource.ts';
Chart.Inject(LineSeries, DataLabel);

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: numData, xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    height: 10, width: 10,
                    dataLabel: { visible: true }
                }
            }
        ],
        // pointRender event for chart
        pointRender: (args: IPointRenderEventArgs) => {
            if(args.point.index === 3){
                args.fill = 'red'
            }
        },
        textRender: (args: ITextRenderEventArgs) => {
            if(args.point.index === 3){
                args.text = 'Maximum Temperature';
                args.color = 'red';
            }
            else {
              args.cancel = true;
            }
        }
}, '#element');

```

{% endtab %}

## See Also

* [Show total stacking values in data label](../chart/how-to/stacking-total/)
* [Prevent the data label when the data value is 0](../chart/how-to/prevent-data-label/#prevent-the-data-label-when-the-data-value-is-0)