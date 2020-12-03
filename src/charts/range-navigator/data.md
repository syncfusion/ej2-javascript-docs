---
title: " RangeNavigator Data | TypeScript "

component: "RangeNavigator"

description: "Range navigator supports double, datetime and logarithmic data values for rendering.Also supports labels and range Customization."
---
<!-- markdownlint-disable MD036 -->

# Types of data

## Numeric

Numeric scale is used to represent the numeric values of data in a chart. By default, the valueType of a range navigator is Double.

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

### Range

Minimum and maximum of the Range navigator will be calculated automatically based on the provided data. You can also customize the range using the minimum, maximum, and interval properties.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries);

let range: RangeNavigator = new RangeNavigator({
   minimum: 10, maximum: 160,interval: 10,
    value:[60,100],
    series: [{
    dataSource: [
      { xData: 10, yData: 35 }, { xData: 20, yData: 28 },
      { xData: 30, yData: 34 }, { xData: 40, yData: 32 },
      { xData: 50, yData: 40 }, { xData: 60, yData: 30 },
      { xData: 70, yData: 4 },  { xData: 80, yData: 22 },
      { xData: 90, yData: 30 },  { xData: 100, yData: 43 },
      { xData: 110, yData: 60 }, { xData: 120, yData: 33 },
      { xData: 130, yData: 40 }, { xData: 140, yData: 29 },
      { xData: 150, yData: 10 }, { xData: 160, yData: 16 },
     ],
    xName: 'xData', yName: 'yData', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

### Label Format

Numeric labels can be formatted using the labelFormat property.

Numeric labels support all globalized formats.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { double } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    labelFormat: 'n1',
    value:[12,30],
    series: [{
    dataSource: double,
    xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

The following table describes the result of applying some commonly used label formats on numeric values.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format property value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>1000</td>
<td>n1</td>
<td>1000.0</td>
<td>The Number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n2</td>
<td>1000.00</td>
<td>The Number is rounded to 2 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>n3</td>
<td>1000.000</td>
<td>The Number is rounded to 3 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p1</td>
<td>1.0%</td>
<td>The Number is converted to percentage with 1 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p2</td>
<td>1.00%</td>
<td>The Number is converted to percentage with 2 decimal place</td>
</tr>
<tr>
<td>0.01</td>
<td>p3</td>
<td>1.000%</td>
<td>The Number is converted to percentage with 3 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c1</td>
<td>$1,000.0</td>
<td>The Currency symbol is appended to number and number is rounded to 1 decimal place</td>
</tr>
<tr>
<td>1000</td>
<td>c2</td>
<td>$1,000.00</td>
<td>The Currency symbol is appended to number and number is rounded to 2 decimal place</td>
</tr>
</table>

### Custom Label Format

The range navigator also supports custom label formats using placeholders such as {value}$, in which, the value
represent the axis label, e.g. 20$.

{% tab template= "rangenavigator/axis", es5Template="es5CustomFormat" %}

```typescript

import { RangeNavigator, StepLineSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, DateTime);
import { double } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    // Custom label format
    labelFormat: '{value}$',
    value:[12,30],
    series: [{
    dataSource: double,
    xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

## Logarithmic Axis

<!-- markdownlint-disable MD033 -->

Logarithmic supports logarithmic scale, and it is used to visualize data when the Range navigator has numerical values
in both lower (e.g.: 10-6) and higher (e.g.: 106) orders of magnitude.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, StepLineSeries, Logarithmic}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, Logarithmic);

let data: object[] = [];
let max: number = 100;
for (let i: number = 0; i < 100; i++) {
    data.push({
        x: Math.pow(10, i * 0.1),
        y: Math.floor(Math.random() * (80 - 30 + 1)) + 30
    });
}
let range: RangeNavigator = new RangeNavigator({
    valueType: 'Logarithmic',
    value: [4,6],
    interval: 1,
    series: [{
                dataSource: data, xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

>Note: To use logarithmic scale,  inject the Logarithmic module using the RangeNavigator.Inject(Logarithmic)
method, and then set the valueType to Logarithmic.

**Range**

Minimum and maximum of the Range navigator will be calculated automatically based on the provided data. You can also customize the range using the minimum, maximum, and interval properties.

{% tab template= "rangenavigator/axis", es5Template="es5LogRange" %}

```typescript

import { RangeNavigator, StepLineSeries, Logarithmic}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, Logarithmic);

let data: object[] = [];
let max: number = 100;
for (let i: number = 0; i < 100; i++) {
    data.push({
        x: Math.pow(10, i * 0.1),
        y: Math.floor(Math.random() * (80 - 30 + 1)) + 30
    });
}
let range: RangeNavigator = new RangeNavigator({
    valueType: 'Logarithmic',
    value: [4,6],
    interval: 1,
    series: [{
                dataSource: data, xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');

```

{% endtab %}

### Logarithmic Base

Logarithmic base can be customized using the logBase property. The default value of the logBase property is 10.

{% tab template= "rangenavigator/axis", es5Template="es5LogBase" %}

```typescript

import { RangeNavigator, StepLineSeries, Logarithmic}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(StepLineSeries, Logarithmic);

let data: object[] = [];
let max: number = 100;
for (let i: number = 0; i < 100; i++) {
    data.push({
        x: Math.pow(10, i * 0.1),
        y: Math.floor(Math.random() * (80 - 30 + 1)) + 30
    });
}
let range: RangeNavigator = new RangeNavigator({
    valueType: 'Logarithmic',
    value: [4,6],
     // logBase for logarithmic scale
    logBase: 2
    series: [{
                dataSource: data, xName: 'x', yName: 'y', type: 'StepLine', width: 2,
            }],
}, '#element');
```

{% endtab %}

## Date-time

Date-time Range navigator supports date-time scale and displays date-time values as a labels in the specified format.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, AreaSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    value:[new Date("2017-08-13"), new Date("2017-12-28")],
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

>Note: Date-time Range navigator supports date-time scale and displays date-time values as a labels in the specified format.

### Interval Customization

Date-time intervals can be customized using the interval and intervalType properties of the range navigator.
For example, when you set interval as 2 and intervalType as years, the interval is considered as 2 years.
Date-time supports the following interval types:
* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, AreaSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    intervalType: 'Months',
    interval: 2,
    value:[new Date("2017-08-13"), new Date("2017-12-28")],
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

**Label Format**

You can format and parse the date to all globalize format using [`labelFormat`](../api/range-navigator/rangeNavigatorAxis/#labelformat-string) property in an axis.

{% tab template= "rangenavigator/axis", es5Template="es5default" %}

```typescript

import { RangeNavigator, AreaSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    labelFormat: 'y/M/d',
    value:[new Date("2017-08-13"), new Date("2017-12-28")],
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

The following table describes the result of applying some common date time formats to the `labelFormat` property

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Label Value</b></td>
<td><b>Label Format Property Value</b></td>
<td><b>Result </b></td>
<td><b>Description </b></td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>EEEE</td>
<td>Monday</td>
<td>The Date is displayed in day format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>yMd</td>
<td>04/10/2000</td>
<td>The Date is displayed in month/date/year format</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td> MMM </td>
<td>Apr</td>
<td>The Shorthand month for the date is displayed</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hm</td>
<td>12:00 AM</td>
<td>Time of the date value is displayed as label</td>
</tr>
<tr>
<td>new Date(2000, 03, 10)</td>
<td>hms</td>
<td>12:00:00 AM</td>
<td>The Label is displayed in hours:minutes:seconds format</td>
</tr>
</table>
