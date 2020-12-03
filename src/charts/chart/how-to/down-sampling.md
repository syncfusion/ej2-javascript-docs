---
title: " Chart Downsampling the data | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Downsampling the chart data

Downsampling is the process of reducing the data rate. We have given a 2000 data points for chart. After applying downsampling algorithm, chart data points has been reduced  and rendered with 400 data points.

Downsampling data using the "Largest-Triangle-Three-Buckets algorithm"[`LTTB`](https://bl.ocks.org/FraserChapman/649f1aba28f6bc941d5c) which describes the point in the bucket that forms the largest triangle using the area of the triangles. This helps to reducing the number of points.

In Downsampling when we perform zooming, particular level of zoomed chart we can see the chart clearly with original data, so we can use original data for that level of zooming. This can be achieved by [`zoomComplete`](../../api/chart/#zoomcomplete) event. Refer the below sample for downsampling with zooming feature.

{% tab template= "chart/chart-appearance", sourceFiles="index.ts,index.html,datasource.ts" , es5Template="es5downsampling" %}

```typescript

import { Chart, LineSeries, Tooltip, getElement, Zoom, Series,IZoomCompleteEventArgs } from '@syncfusion/ej2-charts';
import { downdata } from './datasource.ts';
Chart.Inject(LineSeries, Tooltip, Zoom);

/**
 * Sample for Downsampling
 */

let interval: number;
let chart: Chart = new Chart({
        primaryXAxis: { title: 'Time (s)', majorGridLines: { width: 0 } },
        primaryYAxis: { title: 'Velocity (m/s)', majorGridLines: { width: 0 }, minimum: -15, maximum: 15, interval: 5 },
        series: [
            {
                type: 'Line', xName: 'x', yName: 'y', dataSource: downdata,
                animation: { enable: false }, width: 2
            }
        ],
        chartArea: {
            border: {
                width: 0
            }
        },
        zoomSettings: {
            enableMouseWheelZooming: true,
            enablePinchZooming: true,
            enableSelectionZooming: true,
            mode: 'X',
            enableScrollbar: false
        },
        title: 'Indonesia - Seismograph Analysis',
        tooltip: { enable: false },
        width: '800',
        load: function (args) {
             var threshold = parseInt(args.chart.width) / 8,
              xName = args.chart.series[0].xName,
              yName = args.chart.series[0].yName,
              sampledData = largestTriangleThreeBucket(downdata, threshold, xName, yName);
             args.chart.series[0].dataSource = sampledData;
          },
          zoomComplete: (args: IZoomCompleteEventArgs): void => {
              var zoomComplete:boolean = true;
            if(chart.primaryXAxis.zoomFactor<=0.4)
            {
                chart.series[0].dataSource =downdata;
            }
            else{
               var threshold = parseInt(chart.width) / 8,
               xName = chart.series[0].xName,
               yName = chart.series[0].yName,
               sampledData = largestTriangleThreeBucket(downdata, threshold, xName, yName);
               chart.series[0].dataSource = sampledData;
            }

        }
});
chart.appendTo('#element');

function largestTriangleThreeBucket(data :any, threshold :number, xProperty:any, yProperty:any) {
    yProperty = yProperty || 0;
    xProperty = xProperty || 1;

    var m = Math.floor,
      y = Math.abs,
      f =<number>data.length;

    if (threshold >= f || 0 === threshold) {
      return data;
    }

    var n = [],
      t = 0,
      p = (f - 2) / (threshold - 2),
      c = 0,
      v,
      u,
      w;

    n[t++] = data[c];

    for (var e = 0; e < threshold - 2; e++) {
      for (var g = 0,
        h = 0,
        a = m((e + 1) * p) + 1,
        d = m((e + 2) * p) + 1,
        d = d < f ? d : f,
        k = d - a; a < d; a++) {
        g += +data[a][xProperty], h += +data[a][yProperty];
      }

      for (var g = g / k,
        h = h / k,
        a = m((e + 0) * p) + 1,
        d = m((e + 1) * p) + 1,
        k = +data[c][xProperty],
        x = +data[c][yProperty],
        c = -1; a < d; a++) {
        "undefined" != typeof data[a] &&
          (u = .5 * y((k - g) * (data[a][yProperty] - x) - (k - data[a][xProperty]) * (h - x)),
            u > c && (c = u, v = data[a], w = a));
      }

      n[t++] = v;
      c = w;
    }

    n[t++] = data[f - 1];

    return n;
  };


```

{% endtab %}
**Before applying downsampling algorithm**
![Before applying downsampling algorithm](images/Before_downsampling.png)

**After applying downsampling algorithm**
![After applying downsampling algorithm](images/After_downsampling.png)
