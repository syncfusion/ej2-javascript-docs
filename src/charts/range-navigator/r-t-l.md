---
title: " RangeNavigator Selecting Range | TypeScript "

component: "RangeNavigator"

description: "The range navigator provides RTL (right-to-left) support. Axis labels, series types are rendered right to left when we enabled rtl property."
---

# RTL

The range navigator provides RTL (right-to-left) support. This can be enabled using the “enableRtl” property.

{% tab template= "rangenavigator/reverse", es5Template="es5Rtl" %}

```typescript

import { RangeNavigator, AreaSeries, DateTime}  from "@syncfusion/ej2-charts";
RangeNavigator.Inject(AreaSeries, DateTime);
import { datasrc } from "./datasource.ts";

let range: RangeNavigator = new RangeNavigator({
    valueType: 'DateTime',
    enableRtl: true,
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    labelFormat: 'MMM-yy',
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}
