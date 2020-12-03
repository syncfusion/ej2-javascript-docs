---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Show the total value for stacking series in data label

By using the `annotation`, you can show any element in desired view.

To show the total value in data points, follow the given steps:

**Step 1**:

Define annotation for each x point in chart, now change the annotation value in chart by using
the [`annotationRender`](../../api/chart/chartModel/#annotationrender) event.
In this event, assign the stacked value of the last series to the annotation to show the total value of the
stacking series.

{% tab template= "chart/how-to", es5Template="es5StackingTotal" %}

```typescript

import { ChartAnnotation, Chart, StackingColumnSeries, Category, DataLabel, Tooltip, ILoadedEventArgs,IAnnotationRenderEventArgs, Points } from '@syncfusion/ej2-charts';
Chart.Inject(StackingColumnSeries, ChartAnnotation, DataLabel, Category, Tooltip);
import { EmitType } from '@syncfusion/ej2-base';
    let i: number = 0;
    let chart: Chart = new Chart({
        //Initializing Primary X and Y Axis
        primaryXAxis: {
            valueType: 'Category', interval: 1
        },
        // Initialize the chart series
        series: [
            {
                type: 'StackingColumn', xName: 'x', width: 2, yName: 'y', name: 'Apple', animation: {enable: false},
                dataSource: [{ x: 'Jamesh', y: 5 }, { x: 'Michael', y: 4 }, { x: 'John', y: 5 }],
                marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } }
            }, {
                type: 'StackingColumn', xName: 'x', width: 2, yName: 'y', name: 'Orange',  animation: {enable: false},
                dataSource: [{ x: 'Jamesh', y: 4 }, { x: 'Michael', y: 3 }, { x: 'John', y: 4 }],
                marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } }
            },
            {
                type: 'StackingColumn', xName: 'x', width: 2, yName: 'y', name: 'Grapes', animation: {enable: false},
                dataSource: [{ x: 'Jamesh', y: 1 }, { x: 'Michael', y: 2 }, { x: 'John', y: 2 }],
                marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } }
            }
        ],
        annotations:[
            {
               content: '<div id="point1" style="font-size:11px;font-weight:bold;color:gray;fill:gray;"><span>12</span></div>',
               x: 'Jamesh', y: '11', coordinateUnits: 'Point', region: 'Series'
            },
            {
               content: '<div id="point1" style="font-size:11px;font-weight:bold;color:gray;fill:gray;"><span>12</span></div>',
               x: 'Michael', y: '10', coordinateUnits: 'Point', region: 'Series'
            },
            {
               content: '<div id="point1" style="font-size:11px;font-weight:bold;color:gray;fill:gray;"><span>12</span></div>',
               x: 'John', y: '12', coordinateUnits: 'Point', region: 'Series'
            }
        ],
        // Initialize the chart title
        title: 'Fruit Consumption', tooltip: { enable: true, shared: true },
        annotationRender: (args: IAnnotationRenderEventArgs) => {
          let length = chart.series.length - 1;
          let value = chart.series[length].stackedValues.endValues[i];
          i += (i == length) ? -length : 1;
          args.content.children[0].children[0].innerHTML = value;
        }
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{% endtab %}