---
title: " Chart Localization | TypeScript "

component: "Chart"

description: "Localization library allows to localize the default text content of Chart."
---

# Localization

Localization library allows to localize the default text content of Chart. In Chart component, it has the static text on some features(like zooming toolbars) and this can be changed to any other culture(Arabic, Deutsch, French, etc) by defining the locale value and translation object.

<!-- markdownlint-disable MD033 -->

<table>
<tr>
<td><b>Locale key words</b></td>
<td><b>Text to display</b></td>
</tr>
<tr>
<td>Zoom</td>
<td>Zoom</td>
</tr>
<tr>
<td>ZoomIn</td>
<td>ZoomIn</td>
</tr>
<tr>
<td>ZoomOut</td>
<td>ZoomOut</td>
</tr>
<tr>
<td>Reset</td>
<td>Reset</td>
</tr>
<tr>
<td>Pan</td>
<td>Pan</td>
</tr>
<tr>
<td>ResetZoom</td>
<td>Reset Zoom</td>
</tr>
</table>

To load translation object in an application use load function of L10n class.

For more information about localization, refer this
[`localization`](http://ej2.syncfusion.com/development/react/documentation/base/localization.html).

{% tab template= "chart/internationalization", es5Template="es5Localization" %}

```typescript

import { Chart, ColumnSeries, DataLabel, Zoom } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Zoom);
import { L10n } from '@syncfusion/ej2-base';

let chartData: any[] = [
    { x: 1900, y: 4, y1: 2.6 }, { x: 1920, y: 3.0, y1: 2.8 },
    { x: 1940, y: 3.8, y1: 2.6}, { x: 1960, y: 3.4, y1: 3 },
    { x: 1980, y: 3.2, y1: 3.6 }, { x: 2000, y: 3.9, y1: 3 }
]
L10n.load({
    'ar-AR': {
        'chart': {
            ZoomIn: 'تكبير',
            ZoomOut: 'تصغير',
            Zoom: 'زوم',
            Pan: 'مقلاة',
            Reset: 'إعادة تعيين',
            ResetZoom: ' زومإعادة تعيين'
        },
    }
});
let chart: Chart = new Chart({
    primaryXAxis: {
        title: 'Year',
        edgeLabelPlacement: 'Shift'
    },
    primaryYAxis: {
        title: 'Sales Amount in Millions',
    },
    series:[{
        dataSource: chartData,
        xName: 'x', yName: 'y',
        name: 'Product X', type: 'Column',
        marker: { dataLabel: { visible: true }}
    },{
        dataSource: chartData,
        xName: 'x', yName: 'y1',
        name: 'Product Y', type: 'Column',
         marker: { dataLabel: { visible: true }}
    }],
    title: 'Average Sales Comparison',
    locale: 'ar-AR',
    zoomSettings: {
        enableMouseWheelZooming: true,
        enableDeferredZooming: true,
        enablePinchZooming: true,
        enableSelectionZooming: true
    },
}, '#element');

```

{% endtab %}
