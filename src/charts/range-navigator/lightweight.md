---
title: " RangeNavigator Lightweight | TypeScript "

component: "RangeNavigator"

description: "Lightweight rangenavigator is getting intialized when the datasource for series property is empty."
---

# Lightweight range navigator

By default, when the dataSource for series property in RangeNavigator is empty, a light weight Range navigator will get
initialized without chart. The following code example shows the basic lightweight range navigator.

{% tab template= "rangenavigator/lightweight", es5Template="es5LW" %}

```typescript

import { RangeNavigator, DateTime } from '@syncfusion/ej2-charts';
import { GetDateTimeData } from './datasource.ts';
RangeNavigator.Inject(DateTime);

let range: RangeNavigator = new RangeNavigator(
        {
            valueType: 'DateTime',
            intervalType: 'Months',
            labelFormat: 'MMM',
            value: [new Date(2018, 4, 1), new Date(2018, 8, 1)],
            dataSource: GetDateTimeData(new Date(2018, 0, 1), new Date(2019, 0, 1)),
            xName: 'x', yName: 'y'
        }, '#element');
```

{% endtab %}

## See Also

* [Period Selector](./period-selector/)