---
title: " RangeNavigator Grid and Tick lines | TypeScript "

component: "RangeNavigator"

description: "RangeNavigator supports customization of width, color, and dashArray of the major grid lines using the majorGridLines property."
---

# Grid and Tick Lines

## Grid line customization

You can customize the width, color, and dashArray of the major grid lines using the majorGridLines property.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { double } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    majorGridLines:{
        width: 4,
        color: 'blue',
        dashArray: '5,5'
    },
    value:[25,40],
    series: [{
    dataSource: [
      { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
      { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
      { xData: 50, yData: 40 }
     ],
    xName: 'xData', yName: 'yData', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Tick line customization

You can customize the width, color, and height of the major tick lines using the majorTickLines property.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { double } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
   majorTickLines:{
       width: 3,
       color: 'red'
   },
   value:[25,40],
    series: [{
    dataSource: [
      { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
      { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
      { xData: 50, yData: 40 }
     ],
    xName: 'xData', yName: 'yData', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}