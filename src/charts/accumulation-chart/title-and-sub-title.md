---
title: "Title and SubTitle  | TypeScript "

component: "Accumulation Chart"

description: "Accumulation Chart title and sub title shows information about plotted data"
---

# Title

Accumulation Chart can be given a title using [`title`](../api/accumulation-chart/accumulationChartModel/#title) property, to show the information
about the data plotted.

{% tab template="chart/chart-types", es5Template="es5AccTitle"%}

```typescript

import { AccumulationChart,PieSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(PieSeries);

let pie: AccumulationChart = new AccumulationChart({
  series: [
    {
      dataSource: [
        { x: 'Saudi Arabia', y: 58, text: '58%' },
        { x: 'Persian Gulf', y: 15, text: '15%' },
        { x: 'Canada', y: 13, text: '13%' },
        { x: 'Venezuela', y: 8, text: '8%' },
        { x: 'Mexico', y: 3, text: '3%' },
        { x: 'Russia', y: 2, text: '2%' },
        { x: 'Miscellaneous', y: 1, text: '1%' }
      ],
      xName: 'x', yName: 'y',
      dataLabel: {
        visible: true,
        name: 'text',
        font: { color: 'white' }
      },
    }
  ],
  legendSettings: {
    visible: false,
  },

  title: 'Oil and other liquid imports in USA',
});
pie.appendTo('#element');



```

{% endtab %}

# Title Customization

Accumulation Chart can be customizing a title using [`titleStyle`](../api/accumulation-chart/accumulationChartModel/#titlestyle) property.

{% tab template="chart/chart-types", es5Template="es5AccTitleCus"%}

```typescript

import { AccumulationChart,PieSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(PieSeries);

let pie: AccumulationChart = new AccumulationChart({
  series: [
    {
      dataSource: [
        { x: 'Saudi Arabia', y: 58, text: '58%' },
        { x: 'Persian Gulf', y: 15, text: '15%' },
        { x: 'Canada', y: 13, text: '13%' },
        { x: 'Venezuela', y: 8, text: '8%' },
        { x: 'Mexico', y: 3, text: '3%' },
        { x: 'Russia', y: 2, text: '2%' },
        { x: 'Miscellaneous', y: 1, text: '1%' }
      ],
      xName: 'x', yName: 'y',
      dataLabel: {
        visible: true,
        name: 'text',
        font: { color: 'white' }
      },
    }
  ],
  legendSettings: {
    visible: false,
  },

  title: 'Oil and other liquid imports in USA',
  titleStyle: {
    fontFamily: "Arial",
    fontStyle: 'italic',
    fontWeight: 'regular',
    color: "#E27F2D",
    size: '23px'
  }
});
pie.appendTo('#element');

```

{% endtab %}

## SubTitle

Accumulation Chart can be given a subtitle using [`subTitle`](../api/accumulation-chart/accumulationChartModel/#subtitle) property, to show the information
about the data plotted.

{% tab template="chart/chart-types", es5Template="es5AccSubTitle"%}

```typescript

import { AccumulationChart,PieSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(PieSeries);

let pie: AccumulationChart = new AccumulationChart({
  series: [
    {
      dataSource: [
        { x: 'Saudi Arabia', y: 58, text: '58%' },
        { x: 'Persian Gulf', y: 15, text: '15%' },
        { x: 'Canada', y: 13, text: '13%' },
        { x: 'Venezuela', y: 8, text: '8%' },
        { x: 'Mexico', y: 3, text: '3%' },
        { x: 'Russia', y: 2, text: '2%' },
        { x: 'Miscellaneous', y: 1, text: '1%' }
      ],
      xName: 'x', yName: 'y',
      dataLabel: {
        visible: true,
        name: 'text',
        font: { color: 'white' }
      },
    }
  ],
  legendSettings: {
    visible: false,
  },
  title: 'Oil and other liquid imports in USA',
  subTitle : 'In the year 2014 - 2015'
});
pie.appendTo('#element');

```

{% endtab %}

## SubTitle Customization

Accumulation Chart can be customizing a subtitle using [`subTitleStyle`](../api/accumulation-chart/accumulationChartModel/#subtitlestyle) property, to show the information
about the data plotted.

{% tab template="chart/chart-types", es5Template="es5AccSubTitle"%}

```typescript

import { AccumulationChart,PieSeries} from '@syncfusion/ej2-charts';
AccumulationChart.Inject(PieSeries);

let pie: AccumulationChart = new AccumulationChart({
  series: [
    {
      dataSource: [
        { x: 'Saudi Arabia', y: 58, text: '58%' },
        { x: 'Persian Gulf', y: 15, text: '15%' },
        { x: 'Canada', y: 13, text: '13%' },
        { x: 'Venezuela', y: 8, text: '8%' },
        { x: 'Mexico', y: 3, text: '3%' },
        { x: 'Russia', y: 2, text: '2%' },
        { x: 'Miscellaneous', y: 1, text: '1%' }
      ],
      xName: 'x', yName: 'y',
      dataLabel: {
        visible: true,
        name: 'text',
        font: { color: 'white' }
      },
    }
  ],
  legendSettings: {
    visible: false,
  },
  title: 'Oil and other liquid imports in USA',
  subTitle : 'In the year 2014 - 2015',
  subTitleStyle: {
    fontFamily: "Arial",
    fontStyle: 'italic',
    fontWeight: 'regular',
    color: "#E27F2D",
    size: '13px'
  }
});
pie.appendTo('#element');

```

{% endtab %}
