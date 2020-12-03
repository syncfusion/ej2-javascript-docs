---
title: " Chart Downsampling the data | TypeScript "

component: "Chart"

description: "How to section explains knowledge base samples and howto access different types properties and events of the chart."
---

# Show exact date after scrolling through button click

By using button click you can show exact time or month after scrolling. Here we have changed `zooFactor` and `zoomPosition` based on time or month requirement. After scrolling you want show full month or full day data then you will customize the zoomFactor and zoomPosition of the chart and show exact time or month.

{% tab template= "chart/exact-date", sourceFiles="index.ts,index.html,datasource.ts" , es5Template="es5downsampling" %}

```typescript

import { Chart, LineSeries, DateTime, Legend, Tooltip, ILoadedEventArgs, ChartTheme, Zoom, Crosshair, ScrollBar } from '@syncfusion/ej2-charts';
import { Browser } from '@syncfusion/ej2-base';
import { Internationalization } from '@syncfusion/ej2-base';
Chart.Inject(LineSeries, DateTime, Legend, Tooltip, Crosshair, Zoom, ScrollBar);

let oneDayZoomFactor: Readonly<number> = 1 / 365;
export function numberOfDaysPassed(date: Date) {
  var current: number = +new Date(date.getTime());
  var previous: number = +new Date(date.getFullYear(), 0, 1);
  return Math.ceil((current - previous + 1) / (1000 * 60 * 60 * 24));
}
export function GetDateTimeData(start: Date, end: Date, min?: number, max?: number, inc?: number): object[] {
  let series1: { x: Date, y: number }[] = [];
  let date: number;
  let value: number = 30;
  let option = {
    skeleton: 'full',
    type: 'dateTime'
  };
  let intl: Internationalization = new Internationalization();
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
    let point1: { x: Date, y: number } = { x: new Date(date), y: Math.round(value) };
    if (currentMode === 'Hour') {
      new Date(start.setMinutes(start.getMinutes() + 1));
    } else {
      new Date(start.setDate(start.getDate() + 1));
    }
    series1.push(point1);
  }
  return series1;
}

export function getRandomInt(min: number, max: number): number {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

let data = GetDateTimeData(new Date('1/1/2014'), new Date('12/31/2014'));
let currentMode: string = 'Month';
let chart: Chart = new Chart({
  //Initializing Primary X Axis
  primaryXAxis: {
    title: 'Day',
    valueType: 'DateTime',
    edgeLabelPlacement: 'Shift',
    skeleton: 'short',
    skeletonType: 'Date',
    zoomFactor: oneDayZoomFactor * 31,
    zoomPosition: 0
  },

  //Initializing Primary Y Axis
  primaryYAxis:
  {
    title: 'Server Load',
    labelFormat: '{value}MB'
  },
  height: '350',
  width: '90%',
  crosshair: {
    enable: true, lineType: 'Vertical'
  },

  //Initializing Chart Series
  series: [
    {
      type: 'Line',
      dataSource: data,
      xName: 'x', width: 2, marker: {
        visible: true,
        width: 10,
        height: 10
      },
      yName: 'y', name: 'Germany',
    },

  ],

  //Initializing Chart title
  title: 'Network Load',
  //Initializing User Interaction Tooltip
  tooltip: {
    enable: true, shared: true,
    header: "${point.x}", format: "Server load : ${point.y}"
  },
  load: (args: ILoadedEventArgs) => {
   args.chart.zoomModule.isZoomed = true;
  },
  zoomSettings: {
    mode: 'X',
    toolbarItems: [],
    enableSelectionZooming: true,
    enableScrollbar: true
  },
});

chart.appendTo('#element');
document.getElementById('lastdata').onclick = () => {
  let start: any = new Date(chart.primaryXAxis['visibleRange']['min']);
  if (currentMode === 'Month') {
    let days: number = new Date(start.getFullYear(), start.getMonth() + 1, 0).getDate();
    chart.primaryXAxis.zoomFactor = days * oneDayZoomFactor;
    chart.primaryXAxis.zoomPosition = oneDayZoomFactor * numberOfDaysPassed(new Date(start.getFullYear(), start.getMonth(), 0));
  } else {
    let lastHour: number = Math.floor(chart.primaryXAxis.zoomPosition / chart.primaryXAxis.zoomFactor);
    chart.primaryXAxis.zoomPosition = chart.primaryXAxis.zoomFactor * lastHour;
  }
  chart.dataBind();
};
document.getElementById('chartmode').onclick = () => {
  let modeBtn: HTMLButtonElement = document.getElementById("chartmode") as HTMLButtonElement;
  currentMode = modeBtn.innerHTML.indexOf('Switch To Hour') > -1 ? 'Hour' : 'Month';
  modeBtn.innerHTML = modeBtn.innerHTML.indexOf('Switch To Hour') > -1 ? 'Switch To Year' : 'Switch To Hour';
  document.getElementById('lastdata').innerHTML = 'Last ' + currentMode;
  if (currentMode === 'Hour') {
    let start: any = new Date(chart.primaryXAxis['visibleRange']['min']);
    let monthData: object[] = GetDateTimeData(new Date(start.getFullYear(), start.getMonth(), 1), new Date(start.getFullYear(), start.getMonth(), 2));
    chart.series[0].dataSource = monthData;
    chart.primaryXAxis.zoomFactor = 60 / 1440;
    chart.primaryXAxis.zoomPosition = 0;
    chart.primaryXAxis.skeleton = 'hm';
    chart.primaryXAxis.skeletonType = 'Time';
    chart.dataBind();
  } else {
    chart.series[0].dataSource = GetDateTimeData(new Date('1/1/2014'), new Date('12/31/2014'));
    chart.primaryXAxis.zoomFactor = oneDayZoomFactor * 31;
    chart.primaryXAxis.zoomPosition = 0;
    chart.primaryXAxis.skeleton = 'short';
    chart.primaryXAxis.skeletonType = 'Date';
    chart.dataBind();
  }

};
```

{% endtab %}