---
title: " RangeNavigator Series Types | TypeScript "

component: "RangeNavigator"

description: "Essential JS 2 Range navigator supports 3 types of series, to render the data."
---

# Series Types

Essential JS 2 Range navigator supports 3 types of series, to render the data.

<!-- markdownlint-disable MD036 -->

## Line

<!-- markdownlint-disable MD036 -->

To render a line series, set the series[`type`](../api/range-navigator/rangeNavigatorSeriesModel/#type-string) to `Line`, and
inject the `LineSeries` module using the `RangeNavigator.Inject(LineSeries)` method.

{% tab template= "rangenavigator/axis" %}

```typescript

import { RangeNavigator, DateTime, LineSeries}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject( DateTime, LineSeries);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    labelFormat: 'MMM-yy',
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Line', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Area

To render a step line series, use series [`type`](../api/range-navigator/rangeNavigatorSeriesModel/#type-string) as `Area` and
inject `AreaSeries` module using `RangeNavigator.Inject(AreaSeries)` method.

{% tab template= "rangenavigator/axis" %}

```typescript

import { RangeNavigator, DateTime, AreaSeries}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject( DateTime, AreaSeries);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    labelFormat: 'MMM-yy',
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

## StepLine

To render a step line series, use series [`type`](../api/range-navigator/rangeNavigatorSeriesModel/#type-string) as `StepLine` and
inject `StepLineSeries` module using `RangeNavigator.Inject(StepLineSeries)` method.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { double } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    value:[12,30],
    series: [{
    dataSource: double,
    xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}