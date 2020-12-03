---
title: "Accumulation Chart Tooltip | TypeScript "

component: "Accumulation Chart"

description: "Accumulation chart tooltip represents the x and y values of the current mouse pointer point."
---

# Tooltip

Tooltip for the accumulation chart can be enabled by using the `enable` property.

{% tab template="chart/chart-types", es5Template="es5AccRadius"%}

```typescript

import { AccumulationChart, AccumulationTooltip } from '@syncfusion/ej2-charts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 13, text: 'Jan: 13' }, { x: 'Feb', y: 13, text: 'Feb: 13' },
                         { x: 'Mar', y: 17, text: 'Mar: 17' }, { x: 'Apr', y: 13.5, text: 'Apr: 13.5' }],
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{enable: true}
}, '#element');

```

{% endtab %}

>Note: To use tooltip feature, inject the `AccumulationTooltip` using the `Chart.Inject(AccumulationTooltip)` method.

## Header

We can specify header for the tooltip using `header` property.

{% tab template="chart/chart-types", es5Template="es5AccRadius1"%}

```typescript

import { AccumulationChart, AccumulationTooltip } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{enable: true, header:"Pie Chart"}
}, '#element');

```

{% endtab %}

## Format

By default, tooltip shows information of x and y value in points. In addition to that, you can show more
information in tooltip. For example the format `${series.name} ${point.x}` shows series name and point x value.

{% tab template="chart/chart-types", es5Template="es5AccRadius2"%}

```typescript

import { AccumulationChart, AccumulationTooltip } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{enable: true, format: '${point.x} : <b>${point.y}%</b>' }
}, '#element');

```

{% endtab %}

## Tooltip Format

Any HTML element can be displayed in the tooltip by using the `template` property.

{% tab template="chart/chart-types", es5Template="es5AccRadius3"%}

```typescript

import { AccumulationChart, AccumulationTooltip } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{
            enable: true,
            template:  "<div id='templateWrap' style='background-color:#bd18f9;border-radius: 3px; float: right;padding: 2px;line-height: 20px;text-align: center;'>"+
        "<img src='https://ej2.syncfusion.com/demos/src/chart/images/sunny.png' />" +
        "<div style='color:white; font-family:Roboto; font-style: medium; fontp-size:14px;float: right;padding: 2px;line-height: 20px;text-align: center;padding-right:6px'><span>${y}</span></div></div>" }
}, '#element');

```

{% endtab %}

## Customization

The [`fill`](../api/chart/tooltipSettingsModel/#fill) and
[`border`](../api/chart/tooltipSettingsModel/#border) properties are used to customize the background
color and border of the tooltip respectively. The [`textStyle`](../api/chart/tooltipSettingsModel/#textstyle)
property in the tooltip is used to customize the font of the tooltip text.

{% tab template="chart/chart-types", es5Template="es5AccRadius4"%}

```typescript

import { AccumulationChart, AccumulationTooltip, IAccTooltipRenderEventArgs } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{
            enable: true,
             format: '${series.name} ${point.x} : ${point.y}',
            //fill for tooltip
            fill: '#7bb4eb',
            //border for tooltip
            border: {
                width: 2,
                color: 'grey'
        }
        }
}, '#element');

```

{% endtab %}

## To customize individual tooltip

Using `tooltipRender` event, you can customize a tooltip for particular point. event, you can customize a
tooltip for particular point.

{% tab template="chart/chart-types", es5Template="es5AccRadius5"%}

```typescript

import { AccumulationChart, AccumulationTooltip, IAccTooltipRenderEventArgs } from '@syncfusion/ej2-charts';
import { labelData } from './datasource.ts';
AccumulationChart.Inject(AccumulationTooltip);
let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: labelData,
            xName: 'x',
            yName: 'y'
        }],
        tooltip:{
            enable: true
        },
         tooltipRender: (args: IAccTooltipRenderEventArgs) => {
              if (args.point.index === 3) {
              args.text = args.point.x + '' + ':' + args.point.y + '' + ' ' +'customtext';
              args.textStyle.color = '#f48042';
        }
           }
}, '#element');

```

{% endtab %}