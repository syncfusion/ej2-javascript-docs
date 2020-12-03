---
title: " Chart Appearance | TypeScript "

component: "Chart"

description: "We can set chart size manually by using width and height properties. We can set percentage or pixel size values to the chart."
---

# Chart Dimensions

## Size for Container

Chart can render to its container size. You can set the size via inline or CSS as demonstrated below.

```javascript
    <div id='container'>
        <div id='element' style="width:650px; height:350px;"></div>
    </div>
```

{% tab template= "chart/chart-dimensions", es5="es5Dimensions" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category);
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
        type: 'Line'
    }],
    width:'650px',
    height: '350px'
}, '#element');

```

{% endtab %}
<!-- markdownlint-disable MD036 -->

## Size for Chart

<!-- markdownlint-disable MD036 -->

You can also set size for chart directly through [`width`](../api/chart/#width-string) and [`height`](../api/chart/#height-string) properties.

**In Pixel**

You can set the size of chart in pixel as demonstrated below.

{% tab template= "chart/chart-dimensions", es5Template="es5chartSize" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category);
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
        type: 'Line'
    }],
    // Width and height for chart in pixel
    width: '650', height: '350'
}, '#element');

```

{% endtab %}

**In Percentage**

By setting value in percentage, chart gets its dimension with respect to its container. For example, when
the height is ‘50%’, chart renders to half of the container height.

{% tab template= "chart/chart-dimensions", es5Template="es5ChartSizePercent" %}

```typescript

import { Chart, LineSeries, Category } from '@syncfusion/ej2-charts';
Chart.Inject(LineSeries, Category);
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
        type: 'Line'
    }],
    // Width and height for chart in percentage
    width: '80%', height: '90%'
}, '#element');

```

{% endtab %}

>Note: When you do not specify the size, it takes `450px` as the height and window size as its width.