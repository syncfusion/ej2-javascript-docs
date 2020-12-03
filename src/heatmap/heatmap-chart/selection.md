---
title: "Selection"
component: "HeatMap Chart"
description: "This section describes the cell selection in heatmap"
---

# Selection

In the HeatMap, the cell selection is used to select the single or multiple heat map cells at runtime and get the selected cell details using the [`cellSelected`](../api/heatmap/#cellselected) client side event. You can enable this cell selection using the [`allowSelection`](../api/heatmap/#allowselection) property.

{% tab template= "heatmap/selection", es5Template="es5CellSelection" %}

```typescript

import { HeatMap, Tooltip, ICellEventArgs } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        allowSelection: true,
        dataSource: heatmapData,
});
heatmap.appendTo('#element');
```

{% endtab %}