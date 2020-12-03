---
title: " Chart Working With Data | TypeScript "

component: "Chart"

description: "Chart can be rendered by using different types of data source. They are called local data, remote data and empty points. "
---
<!-- markdownlint-disable MD036 -->

# Working with Data

Chart can visualise data bound from local or remote data.

## Local Data

You can bind a simple JSON data to the chart using
[`dataSource`](../api/chart/series/) property in series. Now map the fields in
JSON to [`xName`](../api/chart/series/#xname-string) and [`yName`](../api/chart/series/#yname-string) properties.

{% tab template= "chart/working-with-data", es5Template="es5LocalData" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category);
let chartData: any[] = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Column'
    }]
}, '#element');

```

{% endtab %}

## Remote Data

You can also bind remote data to the chart using DataManager. The `DataManager` requires minimal information
like webservice URL, adaptor and crossDomain to interact with service endpoint properly. Assign the instance
of DataManager to the [`dataSource`](../api/chart/series/#datasource-object---datamanager) property in series
and map the fields of data to [`xName`](../api/chart/series/#xname-string) and
[`yName`](../api/chart/series/#yname-string) properties. You can also use the
[`query`](../api/chart/series/#query-string) property of the series to filter the data.

{% tab template= "chart/working-with-data", es5Template="es5RemoteData" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { DataManager, Query } from '@syncfusion/ej2-data';
Chart.Inject(ColumnSeries, Category);
let dataManager: DataManager = new DataManager({
    url: 'http://mvc.syncfusion.com/Services/Northwnd.svc/Tasks/'
});
let query: Query = new Query().take(5).where('Estimate', 'lessThan', 3, false);
let chart: Chart = new Chart({
        primaryXAxis: {
            valueType: 'Category',
            title: 'Assignee'
        },
        primaryYAxis:
        {
            title: 'Estimate',
            minimum: 0, maximum: 3, interval: 1
        },
        series: [
            {
                type: 'Column',
                dataSource: dataManager,
                xName: 'Assignee', yName: 'Estimate', query: query,
                name: 'In progress'
            }
        ],
        title: 'Sprint Task Analysis'
}, '#element');

```

{% endtab %}

## Binding Data Using ODataAdaptor

`OData` is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template= "chart/working-with-data", es5Template="es5OData" %}

```typescript

import { Chart, ColumnSeries, Category } from '@syncfusion/ej2-charts';
import { DataManager, Query, ODataAdaptor } from '@syncfusion/ej2-data';
Chart.Inject(ColumnSeries, Category);
let dataManager: DataManager = new DataManager({
   url: 'https://js.syncfusion.com/ejServices/Wcf/Northwind.svc/Orders/?$top=7',
   adaptor: new ej.data.ODataAdaptor()
});
let query: Query = new ej.data.Query();

let chart: Chart = new Chart({
         primaryXAxis: {
            valueType: 'Category'
        },
        //Initializing Chart Sample
        series: [
            {
                type: 'Column',
                dataSource: data,
                xName: 'CustomerID', yName: 'Freight', query: query,
            }
        ],
        title: 'Sprint Task Analysis'
}, '#element');

```

{% endtab %}

## Lazy loading

Lazy loading allows you to load data for chart on demand. Chart will fire the scrollEnd event, in that we can
get the minimum and maximum range of the axis, based on this, we can upload the data to chart.

{% tab template= "chart/working-with-data", es5Template="es5LazyLoading" %}

```typescript

import { Chart,ScrollBar, Zoom, IScrollEventArgs, LineSeries, Tooltip , DateTime} from '@syncfusion/ej2-charts';
import { Internationalization, DateFormatOptions } from '@syncfusion/ej2-base';
Chart.Inject(DateTime, ScrollBar, Zoom, LineSeries, Tooltip);

let intl: Internationalization = new Internationalization();
let chart: Chart = new Chart({
          primaryXAxis: {
            title: 'Day',
            valueType: 'DateTime',
            edgeLabelPlacement: 'Shift',
            skeleton: 'yMMM',
            skeletonType: 'Date',
            scrollbarSettings: {
                range: {
                    minimum: new Date(2009, 0, 1),
                    maximum: new Date(2014, 0, 1)
                },
                enable: true,
            }
        },
        primaryYAxis: {
            title: 'Server Load',
            labelFormat: '{value}MB'
        },
        series: [{
            dataSource: GetDateTimeData(new Date(2009, 0, 1), new Date(2009, 8, 1)),
            xName: 'x', yName: 'y',
            type: 'Line', animation: { enable: false },
        }],
        height: '450',
        title: 'Network Load',
        crosshair: { enable: true, lineType: 'Vertical' },
        tooltip: { enable: true, shared: true },
        legendSettings: { visible: true },
        scrollEnd: (args: IScrollEventArgs) => {
            if (lazymode.value === 'Range') {
                chart.series[0].dataSource = GetDateTimeData(args.currentRange.minimum as Date, args.currentRange.maximum as Date);
            }
            chart.dataBind();
        },
    });
}, '#element');

function GetDateTimeData(start: Date, end: Date): {x: Date, y: number}[] {
        let series1: {x: Date, y: number}[] = [];
        let date: number;
        let value: number = 30;
        let option: DateFormatOptions = {
            skeleton: 'full',
            type: 'dateTime'
        };

        let dateParser: Function = intl.getDateParser(option);
        let dateFormatter: Function = intl.getDateFormat(option);
        for (let i: number = 0; start <= end; i++) {
            date = Date.parse(dateParser(dateFormatter(start)));
            if (Math.random() > .5) {
                value += (Math.random() * 10 - 5);
            } else {
                value -= (Math.random() * 10 - 5);
            }
            if (value < 0) {
                value = getRandomInt(20, 40);
            }
            let point1: {x: Date, y: number} = { x: new Date(date), y: Math.round(value) };
            new Date(start.setDate(start.getDate() + 1));
            series1.push(point1);
        }
        return series1;
    }    function getRandomInt(min: number, max: number): number {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }


```

{% endtab %}

## Empty points

The Data points that uses the `null` or `undefined` as value are considered as empty points. Empty data points are ignored and not plotted in the Chart. When the data is provided by using the points property,
By using `emptyPointSettings` property in series, you can customize the empty point. Default `mode` of the empty point is `Gap`.

{% tab template= "chart/working-with-data", es5Template="es5EmptyPoint" %}

```typescript

import { Chart, ColumnSeries, LineSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, LineSeries, Category);
let chartData: any[] = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: null }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: undefined },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Column',
        emptyPointSettings: {
            mode: 'Gap'
        }
    },
    {
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Line',
        marker: { visible: true},
        emptyPointSettings: {
            mode: 'Average'
        }
    }]
}, '#element');

```

{% endtab %}

**Customizing empty point**

Specific color for empty point can be set by `fill` property in `emptyPointSettings`. Border for a empty point can be set by
`border` property.

{% tab template= "chart/working-with-data", es5Template="es5EmptyPointCus" %}

```typescript

import { Chart, ColumnSeries, LineSeries Category } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, LineSeries, Category);
let chartData: any[] = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: null }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: undefined },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Column',
        emptyPointSettings: {
            mode: 'Average',
            fill: 'green',
            border: { color: 'black', width: 2}
        }
    },
    {
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Line',
        marker: { visible: true},
        emptyPointSettings: {
            mode: 'Zero',
            fill: 'pink'
        }
    }]
}, '#element');

```

{% endtab %}
