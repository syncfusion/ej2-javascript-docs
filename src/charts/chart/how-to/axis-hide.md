---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Hide axis line when clicking the legend

By using the [`chartMouseClick`](../../api/chart/chartModel/#chartmouseclick) event, you can hide the axis line through legend.

To hide the axis line through legend click, follow the given steps:

**Step 1**:

Create a chart with multiple axes.

By using the [`chartMouseClick`](../../api/chart/chartModel/#chartmousemove) event, you can get the legend's target ids. Using this event, you can also get the `yAxisName` of each axis, based on which you can hide the axis line when clicking the legend.

The following code sample demonstrates the output.

{% tab template= "chart/chart-appearance", es5Template="es5sync" %}

```typescript

import {
    Chart, ColumnSeries, IAxisLabelRenderEventArgs, DataLabel, ILoadedEventArgs, Tooltip, Legend, IMouseEventArgs
} from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Tooltip, Legend);

    let chart: Chart = new Chart({
        axes:[
        {
            rowIndex: 0,
            name: 'yAxis',
              opposedPosition: true,
              majorGridLines : {
              width : 0
        },
        },
          {
            rowIndex: 0,
            name: 'yAxis1',
             opposedPosition: true,
              majorGridLines : {
              width : 0
        },
        }
    ],
       margin: {left: 100, right: 100},

        //Initializing Chart Sample
        series: [
            {
                type: 'Column',
                dataSource: [
                    { x: 16, y: 2 }, { x: 17, y: 14 },
                    { x: 18, y: 7 }, { x: 19, y: 7 },
                    { x: 20, y: 10 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'England', fill: '#1e90ff',

            },
             {
                type: 'Column',
                dataSource: [
                    { x: 16, y: 12 }, { x: 17, y: 10 },
                    { x: 18, y: 17 }, { x: 19, y: 20 },
                    { x: 20, y: 16 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'England', fill: 'green', yAxisName: 'yAxis1'

            },
            {
                type: 'Column',
                dataSource: [
                    { x: 16, y: 7 }, { x: 17, y: 7 },
                    { x: 18, y: 11 }, { x: 19, y: 8 },
                    { x: 20, y: 24 }
                ],
                xName: 'x', width: 2,
                yName: 'y', name: 'West Indies', fill: '#b22222',
                  yAxisName: 'yAxis',

            }
        ],
        chartMouseClick: (args: IMouseEventArgs) => {
          if (((args.target).indexOf('chart_legend_text') > -1) || ((args.target).indexOf('chart_legend_shape') > -1) ||
      (args.target).indexOf('chart_legend_shape_marker_') && !(args.target).indexOf('chart_legend_element')) {
      var ids = ((args.target).indexOf('chart_legend_text') > -1) ? (args.target).split('chart_legend_text_')[1].split() :
        args.target.split('chart_legend_shape_marker_')[1] || args.target.split('chart_legend_shape_')[1];
          var chart1 = document.getElementById("element").ej2_instances[0];
        var axesSeriesvisible1 = chart1.axes[0].series[0].visible;
        var axesSeriesvisible2 = chart1.axes[1].series[0].visible;
      if ((chart1.visibleSeries[ids].visible)) {
        if ((chart1.visibleSeries[ids].yAxisName === null)) {
          chart1.primaryYAxis.visible = false;
        } else if ((chart1.visibleSeries[ids].yAxisName === chart1.axes[0].name)) {
          if((!axesSeriesvisible1 && axesSeriesvisible2) || (axesSeriesvisible1 && !axesSeriesvisible2) || (!axesSeriesvisible1 && !axesSeriesvisible2)) {
           chart1.axes[0].visible = false
          } else if(((!axesSeriesvisible1 && axesSeriesvisible2) || (axesSeriesvisible1 && !axesSeriesvisible2) || (axesSeriesvisible1 && axesSeriesvisible1)) && !chart1.axes[1].visible) {
           chart1.axes[1].visible = false;
          }

        }  else if ((chart1.visibleSeries[ids].yAxisName === chart1.axes[1].name)) {
            chart1.axes[1].visible = false;
        }
      } else {
        if ((chart1.visibleSeries[ids].yAxisName === null)) {
         chart1.primaryYAxis.visible = true;
        } else if ((chart1.visibleSeries[ids].yAxisName === chart1.axes[0].name)) {
         if((!axesSeriesvisible1 && axesSeriesvisible2) || (axesSeriesvisible1 && !axesSeriesvisible2) || (!axesSeriesvisible1 && !axesSeriesvisible2)) {
           chart1.axes[0].visible = true
          } else if(((!axesSeriesvisible1 && axesSeriesvisible2) || (axesSeriesvisible1 && !axesSeriesvisible2) || (axesSeriesvisible1 && axesSeriesvisible2)) && !chart1.axes[1].visible) {
            chart1.axes[1].visible = true;
          }
        }  else if ((chart1.visibleSeries[ids].yAxisName === chart1.axes[1].name)) {
            chart1.axes[1].visible = true;
        }
      }
      }

        },
        //Initializing Chart title
        title: 'England vs West Indies',
        //Initializing User Interaction Tooltip
        tooltip: { enable: true, format: '${point.x}th Over : <b>${point.y} Runs</b>' }
    }, '#element');

```

{% endtab %}