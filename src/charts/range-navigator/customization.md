---
title: " RangeNavigator Customization | TypeScript "

component: "RangeNavigator"

description: "Range navigator can be customized using the navigatorBorder, navigatorStyleSettings, seleced or unselected region color properties."
---

# Customization

## Navigator appearance

The navigator can be customized using the “navigatorStyleSettings” property. The “selectedRegionColor” property is used
to specify the color for selected region whereas the “unSelectedRegionColor” property is used to specify the color for
unselected region.

{% tab template= "rangenavigator/getting-started", es5Template="es5Appearance" %}

```typescript

import { RangeNavigator, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    labelFormat: 'MMM-yy',
    navigatorStyleSettings: {
       unselectedRegionColor: 'skyblue',
       selectedRegionColor: 'pink'
        },
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Thumb

The thumb property provides options to customize the border, fill, size, and type of thumb. The types of thumb can be “Circle” and “Rectangle”.

{% tab template= "rangenavigator/getting-started", es5Template="es5Thumb" %}

```typescript

import { RangeNavigator, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    labelFormat: 'MMM-yy',
    navigatorStyleSettings: {
       thumb:{
           type: 'Rectangle',
           border: { width: 2, color: 'red'},
           fill: 'pink'
       }
        },
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Border customization

Using the “navigatorBorder” property, you can customize the “width” and “color” of the range navigator.

{% tab template= "rangenavigator/getting-started", es5Template="es5Border" %}

```typescript

import { RangeNavigator, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    labelFormat: 'MMM-yy',
    navigatorBorder : { width: 4, color: 'green'},
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Deferred update

If the “enableDeferredUpdate” property is set to true, then the changed event will be fired after dragging the slider.
If the “enableDeferredUpdate” is false, then the changed event will be fired when dragging the slider. By default,
the “enableDeferredUpdate” is set to false.

{% tab template= "rangenavigator/deferred", es5Template="es5Deferred" %}

```typescript

import { RangeNavigator, Chart, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
Chart.Inject(DateTime, AreaSeries);
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let chart: Chart = new Chart(
    {
        primaryXAxis: {
            valueType: 'DateTime',
            edgeLabelPlacement: 'Shift'
        },
        series: [{
            dataSource: datasrc, xName: 'x', yName: 'y', width: 2, name: 'Rate', type: 'Area'
        }],
        tooltip: { enable: true },
        height: '350', legendSettings: { visible: false },
    }
);
chart.appendTo('#Chart');
let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    enableDeferredUpdate: true,
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
    changed: (args: IChangedEventArgs) => {
            chart.primaryXAxis.zoomFactor = args.zoomFactor;
            chart.primaryXAxis.zoomPosition = args.zoomPosition;
            chart.dataBind();
        },
}, '#element');

```

{% endtab %}

## Allow snapping

The “allowSnapping” property toggles the placement of the slider exactly to the left or on the nearest interval.

{% tab template= "rangenavigator/getting-started", es5Template="es5Snap" %}

```typescript

import { RangeNavigator, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    labelFormat: 'MMM-yy',
    allowSnapping: true,
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Animation

The speed of the animation can be controlled using the “animationDuration” property. The default value of the “animationDuration” property is 500 milliseconds.

{% tab template= "rangenavigator/getting-started", es5Template="es5Animation" %}

```typescript

import { RangeNavigator, AreaSeries,  DateTime, RangeTooltip}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime, RangeTooltip);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true },
    labelFormat: 'MMM-yy',
    animationDuration: 2000,
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## See Also

* [Grid and Tick Lines](./grid-tick/)
* [Labels](./labels/)