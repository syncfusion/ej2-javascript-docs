---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Show percentage value in pie tooltip

By using the [`tooltipRender`](../../api/accumulation-chart/accumulationChartModel/#tooltiprender) event, you can show the percentage value for each point of pie series in tooltip.

To show the percentage value in pie tooltip, follow the given steps:

**Step 1**:

By using the [`tooltipRender`](../../api/accumulation-chart/accumulationChartModel/#tooltiprender) event, you can get the `args.point.y` and `args.series.sumOfPoints` values.
You can use these values to calculate the percentage value for each point of pie series. To display the percentage value in tooltip, use the `args.content` property.

{% tab template= "chart/how-to", es5Template="es5PercentageTooltip" %}

```typescript
import {
    AccumulationTheme, AccumulationChart, AccumulationLegend, PieSeries, AccumulationTooltip, IAccTooltipRenderEventArgs,
    AccumulationDataLabel
} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationLegend, PieSeries, AccumulationTooltip, AccumulationDataLabel);
let pie: AccumulationChart = new AccumulationChart({
        // Initialize the chart series
    series: [
            {
                dataSource: [
                    { 'x': 'Chrome', y: 37 }, { 'x': 'UC Browser', y: 17 },
                    { 'x': 'iPhone', y: 19 }, { 'x': 'Others', y: 4, text: '4%' }, { 'x': 'Opera', y: 11 }
                ],
                dataLabel:{
                  visible:true
                },
                radius: '70%', xName: 'x',
                yName: 'y', startAngle: 0,
                endAngle: 360, innerRadius: '0%'
            }
        ],
        enableSmartLabels: true,
        legendSettings: {
            visible: false,
        },
        // Initialize tht tooltip
        tooltip: { enable: true },
        title: 'Mobile Browser Statistics',
         tooltipRender: (args: IAccTooltipRenderEventArgs) => {
           let value  = args.point.y / args.series.sumOfPoints * 100;
           args.text = args.point.x + '' + Math.ceil(value) + '' + '%';
        },
        width:'650px',
        height: '350px'
    });
    pie.appendTo('#element');
```

{% endtab %}