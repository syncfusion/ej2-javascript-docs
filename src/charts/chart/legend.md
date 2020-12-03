---
title: " Chart Legend | TypeScript "

component: "Chart"

description: "Chart legend provides information about the series rendered in the chart.It has different alignment, shapes and customization properties. "
---
<!-- markdownlint-disable MD036 -->

# Legend

<!-- markdownlint-disable MD036 -->

Legend provides information about the series rendered in the chart.

## Position and Alignment

By using the [`position`](../api/chart/legendSettings/#position-string) property, you can position the legend
at left, right, top or bottom of the chart. The legend is positioned at the bottom of the chart, by default.

{% tab template= "chart/legend", es5Template="es5Legend" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals',
    legendSettings: {
        visible: true,
        //Legend position as top
        position:'Top'
        }
}, '#element');

```

{% endtab %}

Custom position helps you to position the legend anywhere in the chart using x, y coordinates.

{% tab template= "chart/legend", es5Template="es5LegendPosition" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    legendSettings: {
        visible: true,
        //Legend position as custom
        position:'Custom',
        location: { x: 200, y: 20 } }
}, '#element');

```

{% endtab %}

**Legend Alignment**

You can align the legend as center, far or near to the chart using [`alignment`](../api/chart/legendSettings/#alignment-string) property.

{% tab template= "chart/legend", es5Template="es5LegendAlignment" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column'
    }],
    title: 'Olympic Medals',
    legendSettings: {
        visible: true,
        position:'Top',
        //Legend alignment as near
        alignment: 'Near' }
}, '#element');

```

{% endtab %}

## Customization

To change the legend icon shape, you can use [`legendShape`](../api/chart/series/#legendshape-string) property
in the [`series`](../api/chart/series/). By default legend icon shape is `seriesType`.

{% tab template= "chart/legend", es5Template="es5LegendCust" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column',
        //Legend icon type for chart
        legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        legendShape: 'SeriesType'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        legendShape: 'Rectangle'
    }],
    title: 'Olympic Medals',
    legendSettings: { visible: true }
}, '#element');

```

{% endtab %}

**Legend Size**

By default, legend takes 20% - 25% of the chart's height horizontally, when it is placed on top or bottom position and 20% - 25% of
the width vertically, while placing on left or right position of the chart.
You can change this default legend size by using the
[`width`](../api/chart/legendSettings/#width-string) and [`height`](../api/chart/legendSettings/#height-string) property of the `legendSettings`.

{% tab template= "chart/legend", es5Template="es5LegendSize" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column', legendShape: 'Circle'
    }],
    title: 'Olympic Medals',
    legendSettings: {
         visible: true,
         //Legend size for chart
         width: '500', height: '100',
         border: { width: 1, color: 'pink'}
    }
}, '#element');

```

{% endtab %}

**Legend Item Size**

You can customize the size of the legend items by using the [`shapeHeight`](../api/chart/legendSettings/#shapeheight-number) and
[`shapeWidth`](../api/chart/legendSettings/#shapewidth-number) property.

{% tab template= "chart/legend", es5Template="es5LegendItemSize" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column', legendShape: 'Circle'
    }],
    title: 'Olympic Medals',
    legendSettings: {
         visible: true,
         //Legend item size for chart
         shapeHeight: 10, shapeWidth: 10
    }
}, '#element');

```

{% endtab %}

**Paging for Legend**

Paging will be enabled by default, when the legend items exceeds the legend bounds. You can view each legend
items by navigating between the pages using navigation buttons.

{% tab template= "chart/legend", es5Template="es5LegendPaging" %}

```typescript

import { Chart, LineSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend);
let chartData: any[] = [
    { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
    { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
    { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
    { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
    { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
    { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
];
let chart: Chart = new Chart({
        primaryXAxis: {
            title: 'Countries',
            valueType: 'Category', interval: 1,
            labelIntersectAction : 'Rotate45'
        },
        primaryYAxis:
        {
            title: 'Penetration (%)',
            labelFormat: '{value}%',
            minimum: 0, maximum: 90
        },
        series: [
            {
                type: 'Line', name: 'December 2007',
                dataSource: chartData, xName: 'x', yName: 'y', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Diamond'
                }
            }, {
                type: 'Line', name: 'December 2008',
                dataSource: chartData, xName: 'x', yName: 'y1', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Pentagon'
                }
            }, {
                type: 'Line', name: 'December 2009',
                dataSource: chartData, xName: 'x', yName: 'y2', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Triangle',
                }
            }, {
                type: 'Line', name: 'December 2010',
                dataSource: chartData, xName: 'x', yName: 'y3', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Circle'
                }
            }
        ],
        title: 'FB Penetration of Internet Audience',
        legendSettings: {
            padding: 10, shapePadding: 10,
            visible: true, border: {
                width: 2, color: 'grey'
            },
            width: '200'
        }
}, '#element');

```

{% endtab %}

## Series selection on Legend

By default, legend click enables you to collapse the series visibility.  On other hand, if you need to select
a series through legend click, disable the
[`toggleVisibility`](../api/chart/legendSettings/#togglevisibility-boolean).

{% tab template= "chart/legend" %}

```typescript

import { Chart, ColumnSeries, Category, Legend, Selection } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend, Selection);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column', legendShape: 'Circle'
    }],
    title: 'Olympic Medals',
    selectionMode: 'Series',
    legendSettings: {
         visible: true,
         // series selection on legend
         toggleVisibility: false
    }
}, '#element');

```

{% endtab %}

## Collapsing Legend Item

By default, series name will be displayed as legend. To skip the legend for a particular series, you can give empty string to the series name.

{% tab template= "chart/legend", es5Template="es5LegendCollapse" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
        title: 'Countries'
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        type: 'Column', legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column', legendShape: 'Circle'
    }],
    title: 'Olympic Medals',
    legendSettings: {
         visible: true,
         toggleSeriesVisibility: true
    }
}, '#element');

```

{% endtab %}

## Legend Title

You can set title for legend using `title` property in `legendSettings`. You can also customize the `fontStyle`, `size`, `fontWeight`,
`color`, `textAlignment`, `fontFamily`, `opacity` and `textOverflow` of legend title. `titlePosition` is used to set the legend position in `Top`, `Left` and `Right` position. `maximumTitleWidth` is used to set the width of the legend title. By default, it will be `100px`.

{% tab template= "chart/legend", es5Template="es5LegendTitle" %}

```typescript

import { Chart, ColumnSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, Legend);
let chartData: any[] = [
      { country: "USA", gold: 50, silver: 70, bronze: 45 },
      { country: "China", gold: 40, silver: 60, bronze: 55 },
      { country: "Japan", gold: 70, silver: 60, bronze: 50 },
      { country: "Australia", gold: 60, silver: 56, bronze: 40 },
      { country: "France", gold: 50, silver: 45, bronze: 35 },
      { country: "Germany", gold: 40, silver: 30, bronze: 22 },
      { country: "Italy", gold: 40, silver: 35, bronze: 37 },
      { country: "Sweden", gold: 30, silver: 25, bronze: 27 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        minimum: 0, maximum: 80,
        interval: 20, title: 'Medals'
    },
    series:[{
        dataSource: chartData,
        xName: 'country', yName: 'gold',
        name: 'Gold', type: 'Column',
        //Legend icon type for chart
        legendShape: 'Circle'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'silver',
        name: 'Silver', type: 'Column',
        legendShape: 'SeriesType'
    }, {
        dataSource: chartData,
        xName: 'country', yName: 'bronze',
        name: 'Bronze', type: 'Column',
        legendShape: 'Rectangle'
    }],
    title: 'Olympic Medals',
    legendSettings: { visible: true, title: 'Countries' }
}, '#element');

```

{% endtab %}

## Arrow Page Navigation

By default, the page number will be enabled while legend paging. Now, you can disable that page number and also you can get left and right arrows for page navigation. You have to set `false` value to `enablePages` to get this support.

{% tab template= "chart/legend", es5Template="es5LegendArrowNav" %}

```typescript

import { Chart, LineSeries, Category, Legend } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category, Legend);
let chartData: any[] = [
    { x: 'WW', y: 12, y1: 22, y2: 38.3, y3: 50 },
    { x: 'EU', y: 9.9, y1: 26, y2: 45.2, y3: 63.6 },
    { x: 'APAC', y: 4.4, y1: 9.3, y2: 18.2, y3: 20.9 },
    { x: 'LATAM', y: 6.4, y1: 28, y2: 46.7, y3: 65.1 },
    { x: 'MEA', y: 30, y1: 45.7, y2: 61.5, y3: 73 },
    { x: 'NA', y: 25.3, y1: 35.9, y2: 64, y3: 81.4 }
];
let chart: Chart = new Chart({
        primaryXAxis: {
            title: 'Countries',
            valueType: 'Category', interval: 1,
            labelIntersectAction : 'Rotate45'
        },
        primaryYAxis:
        {
            title: 'Penetration (%)',
            labelFormat: '{value}%',
            minimum: 0, maximum: 90
        },
        series: [
            {
                type: 'Line', name: 'December 2007',
                dataSource: chartData, xName: 'x', yName: 'y', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Diamond'
                }
            }, {
                type: 'Line', name: 'December 2008',
                dataSource: chartData, xName: 'x', yName: 'y1', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Pentagon'
                }
            }, {
                type: 'Line', name: 'December 2009',
                dataSource: chartData, xName: 'x', yName: 'y2', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Triangle',
                }
            }, {
                type: 'Line', name: 'December 2010',
                dataSource: chartData, xName: 'x', yName: 'y3', width: 2,
                marker: {
                    visible: true,
                    width: 10, height: 10,
                    shape: 'Circle'
                }
            }
        ],
        title: 'FB Penetration of Internet Audience',
        legendSettings: {
            width: '180',
            enablePages: false
        }
}, '#element');

```

{% endtab %}

>Note: To use legend feature, we need to inject `Legend` using `Chart.Inject(Legend)`.

## See Also

* [Customize each shape in legend](./how-to/#customize-each-shape-in-legend)