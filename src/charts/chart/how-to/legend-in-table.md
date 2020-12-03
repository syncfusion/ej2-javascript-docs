---
title: " Chart How To | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Add legend in table with x-axis labels

The `annotation` property is used to add legend in table and the `multiLevelLabels` property is used to customize the axis label in table format.

To add legend in table with x-axis labels, follow the given steps:

**Step 1**:

Initialize the custom elements using the `annotation` property.

Create table and rectangle shapes in the html page and set this to the `content` property of annotation.

By setting `coordinateUnits` value to `pixel` in annotation object, you can place the legend in chart based on pixel values.

{% tab template= "chart/legend-table", es5Template="es5legendtable" %}

```typescript

import {  Chart, ColumnSeries, Category, Legend, DataLabel, Tooltip, ILoadedEventArgs, IMouseEventArgs, MultiLevelLabel, IAxisLabelRenderEventArgs, ChartAnnotation } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Category, Legend, Tooltip, MultiLevelLabel, ChartAnnotation);

let columnData: Object[] = [
  { x: 'MWBE', y: 2800000, y1: 1000000 },
  { x: 'LDB', y: 1000000, y1: 1550000 },
  { x: 'VBE', y: 2200000, y1: 1200000 },
  { x: 'DBE', y: 3000000, y1: 1000000 },
  { x: 'MWBE', y: 1000000, y1: 800000 },
  { x: 'LDB', y: 500000, y1: 400000 },
  { x: 'VBE', y: 2100000, y1: 1500000 },
  { x: 'DBE', y: 900000, y1: 0 }
];
let firstClick: Boolean = true;
let chart: Chart = new Chart({
  //Initializing Primary X and Y Axis
  primaryXAxis: {
    valueType: 'Category',
    border: { width: 1, type: 'Rectangle' },
    isIndexed: true,
    interval: 1,
    majorGridLines: { width: 0 },
    multiLevelLabels: [
      {
        border: { type: 'Rectangle' },
        textStyle: { fontWeight: 'Bold' },
        categories: [
          { start: -0.5, end: 3.5, text: 'Construction', },
          { start: 3.5, end: 7.5, text: 'Professional Services', },
        ]
      },
      {
        border: { type: 'Rectangle' },
        categories: [
          { start: -0.5, end: 0.5, text: '248,952,090' },
          { start: 0.5, end: 1.5, text: '248,952,090' },
          { start: 1.5, end: 2.5, text: '248,952,090' },
          { start: 2.5, end: 3.5, text: '248,952,090' },
          { start: 3.5, end: 4.5, text: '248,952,090' },
          { start: 4.5, end: 5.5, text: '248,952,090' },
          { start: 5.5, end: 6.5, text: '248,952,090' },
          { start: 6.5, end: 7.5, text: '248,952,090' },
        ]
      },
      {
        border: { type: 'Rectangle' },
        categories: [
          { start: -0.5, end: 0.5, text: '248,952,090' },
          { start: 0.5, end: 1.5, text: '248,952,090' },
          { start: 1.5, end: 2.5, text: '248,952,090' },
          { start: 2.5, end: 3.5, text: '248,952,090' },
          { start: 3.5, end: 4.5, text: '248,952,090' },
          { start: 4.5, end: 5.5, text: '248,952,090' },
          { start: 5.5, end: 6.5, text: '248,952,090' },
          { start: 6.5, end: 7.5, text: '248,952,090' },
        ]
      },
    ]
  },
  annotations: [
    {
      content: '#templateWrap',
      coordinateUnits: 'Pixel',
      x: 120,
      y: 328
    },
    {
      content: '#templateWrap1',
      coordinateUnits: 'Pixel',
      x: 116,
      y: 300
    },
    {
      content: '#templateWrap2',
      coordinateUnits: 'Pixel',
      x: 116,
      y: 328
    },
  ],
  margin: { left: 100, right: 100 },
  primaryYAxis:
  {
    labelFormat: '{value}%',
  },
  //Initializing Chart Series
  series: [
    {
      type: 'Column', xName: 'x', width: 2, yName: 'y',
      dataSource: columnData, fill: 'skyblue',
      marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } }
    },
    {
      type: 'Column', xName: 'x', width: 2, yName: 'y1', fill: '#b22222',
      dataSource: columnData,
      marker: { dataLabel: { visible: true, position: 'Top', font: { fontWeight: '600', color: '#ffffff' } } }
    },

  ],

  tooltip: { enable: true },
  chartMouseClick: (args: IMouseEventArgs) => {
    if ((args.x >= 83 && args.x <= 155) && (args.y > 312 && args.y < 343)) {
      chart.series[0].dataSource = firstClick ? null : columnData;
      chart.refresh();
      firstClick = !firstClick;
    }

  },
  axisLabelRender: (args: IAxisLabelRenderEventArgs) => {
    if (args.axis.name === 'primaryXAxis') {
      args.text = args.text.split(',')[0];
    }
  }
}, '#element');

```

{% endtab %}