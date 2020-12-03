---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Display the data filtered from grid in pie chart

You can visualize the filtered data that returned by grid in pie chart.

To visualize the data in pie chart, follow the given steps:

**Step 1**:

Initialize the grid with datasource.

**Step 2**:

By using the grid’s `actionComplete` event and `getCurrentViewRecords` method, you can get the current page records. By setting
`allowFiltering` value as `true`, you can filter the data. By using the grid’s `databound` event, you can update the current page
filtered records into the chart’s datasource and display the grid filtered data in chart.

{% tab template= "chart/grid-visual", es5Template="es5GridDataPie" %}

```typescript
import { Grid, Filter, Page, Selection, FilterType, ActionEventArgs  } from '@syncfusion/ej2-grids';
import { orderData } from './datasource.ts';
import { AccumulationChart, ColumnSeries, DateTime, Category, AccumulationDataLabel } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(ColumnSeries, DateTime, Category, AccumulationDataLabel);

Grid.Inject(Filter, Page, Selection);
   let chart: AccumulationChart;
    let filtertype: { [key: string]: Object }[] = [
        { id: 'Menu', type: 'Menu' },
        { id: 'CheckBox', type: 'CheckBox' },
        { id: 'Excel', type: 'Excel' }
    ];

    let grid: Grid = new Grid(
        {
            dataSource: orderData,
            allowPaging: true,
            allowFiltering: true,
            filterSettings: { type: 'Menu' },
            columns: [
                { field: 'OrderID', headerText: 'Order ID', width: 120, textAlign: 'Right' },
                { field: 'CustomerName', headerText: 'Customer Name', width: 150 },
                {
                    field: 'OrderDate', headerText: 'Order Date', width: 130,
                    format: { type: 'dateTime', format: 'M/d/y hh:mm a' }, textAlign: 'Right'
                },
                { field: 'Freight', width: 120, format: 'C2', textAlign: 'Right' }
            ],
            pageSettings: { pageCount: 5 },
            dataBound: () => {
        chart = new AccumulationChart({
           series: [
        {
            dataSource: grid.getCurrentViewRecords(),
            type:'Pie',
            xName: 'CustomerName',
            yName: 'Freight',  dataLabel: { visible: true }
        }
    ]
          });
          chart.appendTo('#Chart');
        },
              actionComplete: (args: ActionEventArgs) => {
              if (args.requestType === 'filtering') {
                 chart.series[0].dataSource =  grid.getCurrentViewRecords();
                   chart.refresh();
                }
              }
        });
    grid.appendTo('#Grid');
```

{% endtab %}