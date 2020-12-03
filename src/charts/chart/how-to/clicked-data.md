---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and how to access different types properties and events of the chart."
---

# Get the data of clicked area in accumulation chart

By using the [`pointClick`](../../api/accumulation-chart#pointClick-emittypeIPointEventArgs) event, you can get the chart data of clicked area.

To show the clicked area data from pie, follow the given steps:

**Step 1**:

By using the [`pointClick`](../../api/accumulation-chart#pointClick-emittypeIPointEventArgs) event, you can get the `args.point.x` and `args.point.y` values.

{% tab template= "chart/how-to", es5Template="es5ClickedData" %}

```typescript
import {
    AccumulationTheme, AccumulationChart, AccumulationLegend, PieSeries, AccumulationTooltip, IAccTooltipRenderEventArgs,IPointEventArgs,
    AccumulationDataLabel
} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationLegend, PieSeries, AccumulationTooltip, AccumulationDataLabel);
let pie: AccumulationChart = new AccumulationChart({
        // Initialize the chart series
        series: [
            {
                dataSource: [
                    { 'x': 'Chrome', y: 37, text: '37%' }, { 'x': 'UC Browser', y: 17, text: '17%' },
                    { 'x': 'iPhone', y: 19, text: '19%' },
                    { 'x': 'Others', y: 4, text: '4%' }, { 'x': 'Opera', y: 11, text: '11%' },
                    { 'x': 'Android', y: 12, text: '12%' }
                ],
                dataLabel: {
                    visible: true, position: 'Inside', name: 'text', font: { fontWeight: '600' }
                },
                radius: '70%', xName: 'x', yName: 'y', startAngle: 0, endAngle: 360, innerRadius: '0%',
                explode: false, explodeOffset: '10%', name: 'Browser', animation: {enable: false}
            }
        ],
        enableAnimation: false,
        legendSettings: { visible: false },
        title: 'Mobile Browser Statistics',
         pointClick:(args: IPointEventArgs) =>{
          document.getElementById("lbl").innerText = "X : "+ args.point.x + "\nY : "+ args.point.y;
        }
    },'#element');
```

{% endtab %}