---
title: "Rendering mode"
component: "HeatMap Chart"
description: "This section describes on how to switch the cell rendering mode between SVG and canvas in heatmap."
---

# Rendering mode

Heat map can be displayed using `Canvas` or `Scalable Vector Graphics (SVG)` rendering logic to improve the initial load performance and scalability.
Heat map can also be automatically switched between `Canvas` and `SVG` modes based on dataset size. You can enable this mode by
setting the [`renderingMode`](../api/heatmap/#renderingmode) property as `Auto`.

> If the `Auto` mode is enabled in the heat map and there are more than 10,000 data points, then the heat map will be rendered in a `Canvas` mode;
Otherwise, the heat map will be rendered in a `SVG` mode.

{% tab template= "heatmap/rendering-mode", es5Template="es5renderMode" %}

```typescript

import { HeatMap, Legend, Tooltip, Adaptor } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Legend, Tooltip, Adaptor);

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
            [74, 33, 88, 23, 86, 59]
        ];

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
    cellSettings: {
            showLabel: true,
        },
    xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
    yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
    renderingMode:"SVG",
    dataSource: heatmapData,
    showTooltip:true,
});
heatmap.appendTo('#element');

```

{% endtab %}
