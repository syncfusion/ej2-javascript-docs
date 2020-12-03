# How To

## Create a Live Chart

You can update a chart with live data by using the set interval.

To update live data in a chart, follow the given steps:

**Step 1**:

Initialize the chart with series.

```javascript
import { Chart } from '@syncfusion/ej2-charts';

// initialize Chart component
let chart: Chart = new Chart(
    //Initializing Chart Series
    series:[
               type: 'Line',
    ]
);
// render initialized Chart
chart.appendTo('#container');
```

**Step 2**:

Update the data to series, and refresh the chart at specified interval by using the set interval.

To refresh the chart, invoke the `refresh` method.

{% tab template= "chart/how-to" %}

```typescript

import { Chart, LineSeries, getElement } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries);
let series1: Object[] = [];
let value: number = 10;
let i: number;
let intervalId: number;

for (i = 0; i < 50; i++) { // Data update
    if (Math.random() > .5) {
        value += Math.random() * 2.0;
    }
    series1[i] = { x: i, y: value };
}

let chart: Chart = new Chart({
        series: [
            {
                type: 'Line',
                dataSource: series1,
                xName: 'x',
                yName: 'y', animation: { enable: false }
            },
        ],
    width:'650px',
    height: '350px'
    },'#element');

    let setTimeoutValue: number = 100;
    intervalId = setInterval(
        (): void => {
if (getElement('container') === null) {
        clearInterval(intervalId);
    } else {
    if (Math.random() > .5) {
        value += Math.random() * 2.0;
    }
    series1.push({ x: i, y: value });
    i++;
    series1.shift(); // Used to remove the first element
    chart.series[0].dataSource = series1;
    chart.refresh();
    }
    }, setTimeoutValue);
```

{% endtab %}

## Prevent the data label when the data value is 0

To prevent the chart data label when the data value is 0, follow the given steps:

**Step 1**:

Get the point value and check whether the `args.point.y` value is zero or not by using the [`textRender`](https://ej2.syncfusion.com/documentation/api/chart/iTextRenderEventArgs/) event.
If the value is zero, then set the `args.cancel` to true.

The output will appear as follows,

{% tab template= "chart/how-to" %}

```typescript
import { Chart, LineSeries, DateTime, ITextRenderEventArgs, DataLabel } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, DateTime, DataLabel);
let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'DateTime',
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2005, 0, 1), y: 21 }, { x: new Date(2006, 0, 1), y: 24 },
                    { x: new Date(2007, 0, 1), y: 0 }, { x: new Date(2008, 0, 1), y: 38 },
                    { x: new Date(2009, 0, 1), y: 54 }, { x: new Date(2010, 0, 1), y: 57 },
                ],
                xName: 'x', width: 2, marker: {
                  dataLabel : { visible: true },
                    visible: true,
                    width: 10,
                    height: 10
                },
                yName: 'y', name: 'Germany',
            }
        ],

        //Initializing Chart title
        title: 'Inflation - Consumer Price',
        textRender: (args: ITextRenderEventArgs) => {
          args.cancel = args.point.y === 0;
        }
    width:'650px',
    height: '350px'
},'#element');
```

{% endtab %}

## Format the tooltip value

Using [`tooltipRender`](https://ej2.syncfusion.com/documentation/api/chart/iTooltipRenderEventArgs/) event, you can able to format the
datetime value instead of rendered value.

To format the datetime value,please follow the steps below

**Step 1**:

By using [`tooltipRender`](https://ej2.syncfusion.com/documentation/api/chart/iTooltipRenderEventArgs/) event we can able to get
the current point x value. Using this value to format the tooltip by using `formatDate` method.

The output will appear as follows,

{% tab template= "chart/how-to" %}

```typescript
import { Chart, LineSeries, DateTime,  ITooltipRenderEventArgs, DataLabel, Tooltip } from '@syncfusion/ej2-charts';
import { Internationalization } from '@syncfusion/ej2-base';
Chart.Inject(LineSeries, DateTime, DataLabel, Tooltip);
let chart: Chart = new Chart({

        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'DateTime',
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [
                    { x: new Date(2005, 0, 1), y: 21 }, { x: new Date(2006, 0, 1), y: 24 },
                    { x: new Date(2007, 0, 1), y: 30 }, { x: new Date(2008, 0, 1), y: 38 },
                    { x: new Date(2009, 0, 1), y: 54 }, { x: new Date(2010, 0, 1), y: 57 },
                ],
                xName: 'x', width: 2, marker: {
                  dataLabel : { visible: true },
                    visible: true,
                    width: 10,
                    height: 10
                },
                yName: 'y', name: 'Germany',
            }
        ],

       //Initializing Chart title
        title: 'Inflation - Consumer Price',
        tooltip: {enable: true},
        tooltipRender:(args: ITooltipRenderEventArgs) => {  //  To format the current point x value
        let intl: Internationalization = new Internationalization();
        let formattedString: string = intl.formatDate(new Date(args.point.x), { skeleton: 'yMd' });
        args.text = formattedString;
        };
    width:'650px',
    height: '350px'
},'#element');
```

{% endtab %}

## Add or remove a series from the chart dynamically

You can add or remove the chart series dynamically by using the `addSeries` or `removeSeries` method.

To add or remove the series dynamically, follow the given steps:

**Step 1**:

To add a new series to chart dynamically, pass the series value to the `addSeries` method.

To remove the new series from chart dynamically, pass the series index to the `removeSeries` method.

{% tab template= "chart/add-series" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
import { Button } from '@syncfusion/ej2-buttons';
import { EmitType } from '@syncfusion/ej2-base';

let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Manager',
            valueType: 'Category',

        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Sales',
            minimum: 0,
            maximum: 20000,
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Column',
                dataSource: [{ x: 'John', y: 10000 }, { x: 'Jake', y: 12000 }, { x: 'Peter', y: 18000 },
                { x: 'James', y: 11000 }, { x: 'Mary', y: 9700 }],
                xName: 'x', width: 2,
                yName: 'y'
            }
        ],
        //Initializing Chart title
        title: 'Sales Comparision',
    }, '#element');

    document.getElementById('add').onclick = () => {
        chart.addSeries([{
                type: 'Column',
                dataSource: [{ x: 'John', y: 11000 }, { x: 'Jake', y: 16000 }, { x: 'Peter', y: 19000 },
                { x: 'James', y: 12000 }, { x: 'Mary', y: 10700 }],
                xName: 'x', width: 2,
                yName: 'y'
            }]);
    };
     document.getElementById('remove').onclick = () => {
        chart.removeSeries(1);
    };
```

{%endtab%}

## Customize the series points by using patterns

You can customize the series points with patterns by using the `pointColorMapping` property.

To customize the series point colors, follow the given steps:

**Step 1**:

Define the patterns and map the pattern URL to the series point using `pointColorMapping` property in series.

{% tab template= "chart/pattern-point" %}

```typescript

import { Chart, ColumnSeries, Category, DataLabel, Tooltip } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DataLabel, Category, Tooltip);
import { EmitType } from '@syncfusion/ej2-base';

    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            minimum: 0, maximum: 250, interval: 50
        },

        //Initializing Chart Series
        series: [
            {
                type: 'Column', xName: 'x', width: 2, yName: 'y', pointColorMapping: 'color',
                dataSource: [
                    { x: 'BGD', y: 106, text: 'Bangaladesh', color:  'url(#chess)' },
                    { x: 'BTN', y: 103, text: 'Bhutn',  color:  'url(#cross)' },
                    { x: 'NPL', y: 198, text: 'Nepal',  color: 'url(#circle)' },
                    { x: 'THA', y: 189, text: 'Thiland',  color:  'url(#rectangle)' },
                    { x: 'MYS', y: 230, text: 'Malaysia',  color: 'url(#line)' }
                ], name: 'Tiger',
                cornerRadius: {
                    bottomLeft: 10, bottomRight: 10, topLeft: 10, topRight: 10
                }
            }
        ],
        legendSettings: { visible: false },
        //Initializing Chart title
        title: 'Tiger Population - 2016',
    width:'650px',
    height: '300px'
    },'#element');
```

{%endtab%}

## Show the total value for stacking series in data label

By using the `annotation`, you can show any element in desired view.

To show the total value in data points, follow the given steps:

**Step 1**:

Define annotation for each x point in chart, now change the annotation value in chart by using
the [`annotationRender`](https://ej2.syncfusion.com/documentation/api/chart/iAnnotationRenderEventArgs/) event.
In this event, assign the stacked value of the last series to the annotation to show the total value of the
stacking series.

{% tab template= "chart/how-to" %}

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

{%endtab%}

## Display selected data for range selection

By using the [`dragComplete`](https://ej2.syncfusion.com/documentation/api/chart/iDragCompleteEventArgs/), you can get the selected data values for range selection.

To display the selected data value, follow the given steps:

**Step 1**:

Get the selected data point values and display the values through grid component by using the [`dragComplete`](https://ej2.syncfusion.com/documentation/api/chart/iDragCompleteEventArgs/) event.

{% tab template= "chart/how-to" %}

```typescript

import { Chart, Selection } from '@syncfusion/ej2-charts';
import { Legend, Category, ScatterSeries } from '@syncfusion/ej2-charts';
Chart.Inject(Selection, Legend, Category, ScatterSeries);
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let selectedData: any;
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            minimum: 1970,
            maximum: 2016
        },
        //Initializing Primary Y Axis
        primaryYAxis: {
            title: 'Sales',
            labelFormat: '{value}%',
            interval: 25,
            minimum: 0,
            maximum: 100,
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Scatter',
                dataSource: [{ x: 1971, y: 50 }, { x: 1972, y: 20 }, { x: 1973, y: 63 }, { x: 1974, y: 81 }, { x: 1975, y: 64 },
                    { x: 1976, y: 36 }, { x: 1977, y: 22 }, { x: 1978, y: 78 }, { x: 1979, y: 60 }, { x: 1980, y: 41 },
                    { x: 1981, y: 62 }, { x: 1982, y: 56 }, { x: 1983, y: 96 }, { x: 1984, y: 48 }, { x: 1985, y: 23 },
                    { x: 1986, y: 54 }, { x: 1987, y: 73 }, { x: 1988, y: 56 }, { x: 1989, y: 67 }, { x: 1990, y: 79 },
                    { x: 1991, y: 18 }, { x: 1992, y: 78 }, { x: 1993, y: 92 }, { x: 1994, y: 43 }, { x: 1995, y: 29 },
                    { x: 1996, y: 14 }, { x: 1997, y: 85 }, { x: 1998, y: 24 }, { x: 1999, y: 61 }, { x: 2000, y: 80 },
                    { x: 2001, y: 14 }, { x: 2002, y: 34 }, { x: 2003, y: 81 }, { x: 2004, y: 70 }, { x: 2005, y: 21 },
                    { x: 2006, y: 70 }, { x: 2007, y: 32 }, { x: 2008, y: 43 }, { x: 2009, y: 21 }, { x: 2010, y: 63 },
                    { x: 2011, y: 9 }, { x: 2012, y: 51 }, { x: 2013, y: 25 }, { x: 2014, y: 96 }, { x: 2015, y: 32 }
                ],
                xName: 'x',
                yName: 'y', name: 'Product A',
                marker: {
                    shape: 'Triangle',
                    width: 10, height: 10
                }
            }
        ],
        title: 'Profit Comparision of A and B', legendSettings: { visible: true, toggleVisibility: false },
        selectionMode: 'DragXY',
        //Get selected range data values
        dragComplete:(args: IDragCompleteEventArgs) => {
        grid.dataSource = args.selectedDataValues[0];
        grid.refresh();
        }
    });
    chart.appendTo('#element');
    let grid: Grid = new Grid({
    columns: [
                { field: 'x', headerText: 'x',  type: 'string' },
                { field: 'y', headerText: 'y', type: 'number' }
    ],
   });
   grid.appendTo('#Grid');
```

{%endtab%}

## Customize the marker with different shape

By using the [`pointRender`](https://ej2.syncfusion.com/documentation/api/chart/iPointEventArgs/), you can customize the marker shape.

To Customize the marker shape, follow the given steps:

**Step 1**:

Customize the marker shape in each data point by using the [`pointRender`](https://ej2.syncfusion.com/documentation/api/chart/iPointEventArgs/) event. Using this event, you can set the `shape` value to the argument.

{% tab template= "chart/how-to" %}

```typescript

import { Chart, LineSeries, Category,IPointRenderEventArgs, Legend,ILoadedEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend);
let shapes: string[] = [
   'Diamond', 'Circle','Rectangle', 'Line', 'Triangle', 'Rectangle'
   ];
let shapeRender: EmitType<IPointRenderEventArgs> = (args: IPointRenderEventArgs)=> {
 args.shape = shapes[args.point.index];
 };
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            title: 'Countries', valueType: 'Category',
            interval: 1
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Penetration', rangePadding: 'None',
            labelFormat: '{value}%', minimum: 0,
            maximum: 75, interval: 15
        }
        //Initializing Chart Series
        series: [
            {
                type: 'Line',
                dataSource: [{ x: 'WW', y: 12, text: 'World Wide' },
                { x: 'EU', y: 5, text: 'Europe' },
                { x: 'APAC', y: 15, text: 'Pacific' },
                { x: 'LATAM', y: 6.4, text: 'Latin' },
                { x: 'MEA', y: 30, text: 'Africa' },
                { x: 'NA', y: 25.3, text: 'America' }],
                name: 'December 2007',
                marker: {
                    visible: true, width: 10, height: 10,
                    shape: 'Diamond', dataLabel: { name: 'text' }
                },
                xName: 'x', width: 2,
                yName: 'y',
            },

        ],
        //Initializing Chart title
        title: 'FB Penetration of Internet Audience',
        legendSettings: { visible: false },
        pointRender: shapeRender,
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{%endtab%}

## Customize each shape in legend

By using the [`legendRender`](https://ej2.syncfusion.com/documentation/api/chart/iLegendRenderEventArgs/), you can customize the legend shape.

To Customize the legend shape, follow the given steps:

**Step 1**:

Set the shape value for each legend using `args.shape` in [`legendRender`](https://ej2.syncfusion.com/documentation/api/chart/iLegendRenderEventArgs/) event.

{% tab template= "chart/how-to" %}

```typescript

import { Chart, StepAreaSeries, Legend, ILoadedEventArgs, ILegendRenderEventArgs } from '@syncfusion/ej2-charts';
Chart.Inject(StepAreaSeries, Legend);
    let chart: Chart = new Chart({
      //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Double',
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            title: 'Production (Billion as kWh)',
            valueType: 'Double'
        },
        //Initializing Chart Series
        series: [
            {
                type: 'StepArea',
                dataSource: [{ x: 2000, y: 416 }, { x: 2001, y: 490 }, { x: 2002, y: 470 }, { x: 2003, y: 500 },
                { x: 2004, y: 449 }, { x: 2005, y: 470 }, { x: 2006, y: 437 }, { x: 2007, y: 458 }],
                name: 'Renewable',
                xName: 'x', width: 2,
                yName: 'y',
            },
            {
                type: 'StepArea',
                dataSource: [{ x: 2000, y: 180 }, { x: 2001, y: 240 }, { x: 2002, y: 370 }, { x: 2003, y: 200 },
                { x: 2004, y: 229 }, { x: 2005, y: 210 }, { x: 2006, y: 337 }, { x: 2007, y: 258 }],
                name: 'Non-Renewable',
                xName: 'x', width: 2,
                yName: 'y',
            },
        ],
        //Initializing Chart title
    title: 'Electricity- Production',
    legendRender: (args: ILegendRenderEventArgs)=> {
    if (args.text === 'Renewable') {
    args.shape = 'Circle';
    } else if (args.text === 'Non-Renewable') {
    args.shape = 'Triangle';
    }
    },
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{%endtab%}

## Create a table in tooltip

You can show the tooltip as table by using template property in tooltip.

Follow the given steps to show the table tooltip,

**Step 1**:

Initialize the tooltip template div as shown in the following html page,

```html
    <div id='templateWrap'>
        <table style="width:100%;  border: 1px solid black;">
        <tr><th colspan="2" bgcolor="#00FFFF">Female</th></tr>
        <tr><td bgcolor="#00FFFF">${x}:</td><td bgcolor="#00FFFF">${y}</td></tr>
        </table>
    </div>

```

**Step 2**:

To show that tooltip template, set the element id to the `template` property in tooltip.

{% tab template= "chart/table" %}

```typescript
import {
    Chart, LineSeries, Legend, Category, Tooltip
} from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend,Tooltip);
import { Browser } from '@syncfusion/ej2-base';

let chart: Chart = new Chart({
        title: 'Population of India ( 2010 - 2016 )',
        // Initialize the chart axes
        primaryXAxis: {
            minimum: 2010, maximum: 2016,
            edgeLabelPlacement: 'Shift',

        },
        primaryYAxis: {
            minimum: 900, maximum: 1300,
            labelFormat: '{value}M',
        },
        // Initialize the chart series
        series: [
           {
                name: 'Female',
                dataSource: [
                    { x: 2010, y: 990 }, { x: 2011, y: 1010 },
                    { x: 2012, y: 1030 }, { x: 2013, y: 1070 },
                    { x: 2014, y: 1105 }, { x: 2015, y: 1138 },
                    { x: 2016, y: 1155 }
                ], xName: 'x', yName: 'y',
                marker: {
                    visible: true,
                    shape: 'Rectangle',
                    width: 2
            }
        ],
        tooltip: {
            enable: true,
            template:'#Female-Material'
        },
    width:'650px',
    height: '350px'
    });
    chart.appendTo('#element');
```

{%endtab%}

## Create footer and watermark for chart

By using `annotation`, you can place any html elements to chart in a desired view.

To create footer and watermark for chart, follow the given steps:

**Step 1**:

Initialize the custom elements by using the `annotation` property.

By using the `content` option of the annotation object, you can specify the id of the element that needs to be displayed in the chart area as follow,

{% tab template= "chart/table" %}

```typescript
import { Chart, SplineSeries, ChartAnnotation, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(SplineSeries, Category, Legend, ChartAnnotation);
let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
            interval: 1, majorGridLines: { width: 0 },
            labelIntersectAction: 'Rotate90'
        },
        //Initializing Annotations
        annotations: [{ // watermark for chart
            content: '<div id="chart_cloud" style="font-size:450%; opacity: 0.3;" >syncfusion</div>',
            x: 'Wed', y: 20, coordinateUnits: 'Point', horizontalAlignment: 'Center'
        },{ //footer for chart
            content: '<div id="chart" > <a href="https://www.syncfusion.com" target="_blank">www.syncfusion.com</a></div>',
            x: 400, y: 340, coordinateUnits: 'Pixel', horizontalAlignment: 'Center'
        }
        ],
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            minimum: 0,
            maximum: 40,
            interval: 10,
        },
        //Initializing Chart Series
        series: [
            {
                type: 'Spline',
                dataSource: [
                    { x: 'Sun', y: 15 }, { x: 'Mon', y: 5 },{ x: 'Tue', y: 32 },
                    { x: 'Wed', y: 15 },{ x: 'Thu', y: 29 }, { x: 'Fri', y: 24 },
                    { x: 'Sat', y: 18 },
                ],
                xName: 'x', width: 2, marker: {
                    visible: true
                },
                yName: 'y', name: 'Max Temp',
            }

        ],
        //Initializing Chart title
        title: 'NC Weather Report - 2016',
        width:'650px',
        height: '350px'
    });
    chart.appendTo('#element');
```

{%endtab%}

## Mark a threshold in chart

You can mark a threshold in chart by using the `stripline`.

To mark a threshold in chart, follow the given steps:

**Step 1**:

By using the start and end properties of `striplines` object in vertical axis, you can mark the threshold
for y values of the series.

{% tab template= "chart/how-to" %}

```typescript
import { Chart, LineSeries, Category, Legend, Tooltip, ILoadedEventArgs, StripLine, ChartTheme } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend, Tooltip, StripLine);
    let chart: Chart = new Chart({
        //Initializing Primary X Axis
        primaryXAxis: {
            valueType: 'Category',
        },
        //Initializing Primary Y Axis
        primaryYAxis:
        {
            minimum: 10, maximum: 40, interval: 5,
            lineStyle: { color: '#808080' }, labelFormat: '{value} °C', rangePadding: 'None',
            //Initializing Striplines
            stripLines: [
                {
                    start: 30, end: 30.1, color: '#ff512f', visible: true,
                    textStyle: { size: '18px', color: '#ffffff', fontWeight: '600' },
                }
            ]
        },
        //Initializing Chart Series
        series: [
            {
                dataSource: [
                    { x: 'Sun', y: 28 }, { x: 'Mon', y: 27 }, { x: 'Tue', y: 33 }, { x: 'Wed', y: 36 },
                    { x: 'Thu', y: 28 }, { x: 'Fri', y: 30 }, { x: 'Sat', y: 31 }],
                xName: 'x', width: 2, yName: 'y',  type: 'Line', name: 'Weather',
                marker: { visible: true, width: 10, height: 10, border: { width: 2, color: '#ffffff' }, fill: '#666666' },
            },
        ],
        legendSettings: { visible: false },
        //Initializing Chart Title
        title: 'Weather Report',
        width:'650px',
        height: '350px'
    });
    chart.appendTo('#element');
```

{%endtab%}

## Visualize the data that returned by grid in chart

You can visualize the data that returned by grid in chart.

To visualize the data in chart, follow the given steps:

**Step 1**:

Initialize the grid with datasource.

**Step 2**:

By using the grid’s `actionComplete` event and `getCurrentViewRecords` method, you can get the current page records.
By using the grid’s `databound` event, you can update the current page records into the chart’s datasource and visualize the grid data in chart.

{% tab template= "chart/grid-visual" %}

```typescript
import { Grid, Selection, Page,  ActionEventArgs } from '@syncfusion/ej2-grids';
import { Query, DataManager } from '@syncfusion/ej2-data';
import { orderData } from './datasource.ts';
import { Chart, ColumnSeries, DateTime } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, DateTime);
Grid.Inject(Selection,Page);
    let chart: Chart;
    let data: Object = new DataManager(orderData as JSON[]).executeLocal(new Query().take(100));
    let grid: Grid = new Grid(
        {
            dataSource: data,
            allowPaging: true,
            pageSettings: { pageSize: 10 },
            columns: [
                { field: 'OrderDate', headerText: 'Order Date', width: 130, format: 'yMd', textAlign: 'right' },
                { field: 'Freight', width: 120, format: 'C2', textAlign: 'right' }
            ],
        dataBound: () => {
        chart = new Chart({
            //Initializing Primary X Axis
            primaryXAxis: {
            valueType: 'DateTime',
            },
            series: [
            {
                type: 'Column',
                dataSource: grid.getCurrentViewRecords(),
                xName: 'OrderDate', width: 2, marker: {
                    visible: true,
                    width: 10,
                    height: 10
                },
                yName: 'Freight', name: 'Germany',
            },
        ],
        width:'650px',
        height: '350px'
          });
          chart.appendTo('#Chart');
        },
         actionComplete: (args: ActionEventArgs) => {
                if (args.requestType === 'paging') {
                 chart.series[0].dataSource =  grid.getCurrentViewRecords();
                   chart.refresh();
                }
        });
    grid.appendTo('#Grid');
```

{%endtab%}

## Show percentage value in pie tooltip

By using the [`tooltipRender`](https://ej2.syncfusion.com/documentation/api/accumulation-chart/iAccTooltipRenderEventArgs/) event, you can show the percentage value for each point of pie series in tooltip.

To show the percentage value in pie tooltip, follow the given steps:

**Step 1**:

By using the [`tooltipRender`](https://ej2.syncfusion.com/documentation/api/accumulation-chart/iAccTooltipRenderEventArgs/) event, you can get the `args.point.y` and `args.series.sumOfPoints` values.
You can use these values to calculate the percentage value for each point of pie series. To display the percentage value in tooltip, use the `args.content` property.

{% tab template= "chart/how-to" %}

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

{%endtab%}