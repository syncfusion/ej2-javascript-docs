---
title: " RangeNavigator Period Selector | TypeScript "

component: "RangeNavigator"

description: "The period selector allows to select a range with specified periods."
---

# Period selector

The period selector allows to select a range with specified periods.

## Periods

Periods is an array of objects that allows users to specify the range of periods. The “interval” property specifies the count value of the button, and the “text” property specifies the text to be displayed on button. The “intervalType” property allows users to customize the intervals of the buttons. The “intervalType” property supports the following interval types:

* Auto
* Years
* Quarter
* Months
* Weeks
* Days
* Hours
* Minutes
* Seconds

{% tab template= "rangenavigator/periodselector" %}

```typescript

import { RangeNavigator, Chart, IChangedEventArgs, PeriodSelector, AreaSeries, DateTime, PeriodSelectorSettingsModel } from '@syncfusion/ej2-charts';

RangeNavigator.Inject(
    PeriodSelector, DateTime, AreaSeries
);
import { chartData } from './datasource.ts';
let periodsValue: PeriodSelectorSettingsModel = {
    periods: [
        { text: '1M', interval: 1, intervalType: 'Months' }, { text: '3M', interval: 3, intervalType: 'Months' },
        { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
        { text: '1Y', interval: 1, intervalType: 'Years' },
        { text: '2Y', interval: 2, intervalType: 'Years', selected: true
         },
        { text: 'All' }
    ]
};
let range: RangeNavigator = new RangeNavigator(
        {
        valueType: 'DateTime',
        series: [
            {
                dataSource: chartData,
                xName: 'x', yName: 'close', type: 'Area', width: 2,

            }
        ], periodSelectorSettings: periodsValue,
        }, '#element');
```

{% endtab %}

>Note: To use the period selector feature, inject the PeriodSelector module using the RangeNavigator.Inject(PeriodSelector)
method.

## Positioning period selector

The “position” property allows users to position the period selector either at the “top” or “bottom”.

{% tab template= "rangenavigator/periodselector" %}

```typescript

import { RangeNavigator, Chart, IChangedEventArgs, PeriodSelector, AreaSeries, DateTime, PeriodSelectorSettingsModel } from '@syncfusion/ej2-charts';

RangeNavigator.Inject(
    PeriodSelector, DateTime, AreaSeries
);
import { chartData } from './datasource.ts';
let periodsValue: PeriodSelectorSettingsModel = {
    position: 'Top',
    periods: [
        { text: '1M', interval: 1, intervalType: 'Months' }, { text: '3M', interval: 3, intervalType: 'Months' },
        { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
        { text: '1Y', interval: 1, intervalType: 'Years' },
        { text: '2Y', interval: 2, intervalType: 'Years', selected: true
         },
        { text: 'All' }
    ]
};
let range: RangeNavigator = new RangeNavigator(
        {
        valueType: 'DateTime',
        series: [
            {
                dataSource: chartData,
                xName: 'x', yName: 'close', type: 'Area', width: 2,

            }
        ], periodSelectorSettings: periodsValue,
        }, '#element');
```

{% endtab %}

## Height

The “height” property allows users to specify the height for period selector. The default value of the height property is 43.

{% tab template= "rangenavigator/periodselector" %}

```typescript

import { RangeNavigator, Chart, IChangedEventArgs, PeriodSelector, AreaSeries, DateTime, PeriodSelectorSettingsModel } from '@syncfusion/ej2-charts';
import { EmitType } from '@syncfusion/ej2-base';

RangeNavigator.Inject(
    PeriodSelector, DateTime, AreaSeries
);
import { chartData } from './datasource.ts';
let periodsValue: PeriodSelectorSettingsModel = {
    height: 65,
    periods: [
        { text: '1M', interval: 1, intervalType: 'Months' }, { text: '3M', interval: 3, intervalType: 'Months' },
        { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
        { text: '1Y', interval: 1, intervalType: 'Years' },
        { text: '2Y', interval: 2, intervalType: 'Years', selected: true
         },
        { text: 'All' }
    ]
};
let range: RangeNavigator = new RangeNavigator(
        {
        valueType: 'DateTime',
        series: [
            {
                dataSource: chartData,
                xName: 'x', yName: 'close', type: 'Area', width: 2,

            }
        ], periodSelectorSettings: periodsValue,
        }, '#element');
```

{% endtab %}

## Visibility of range navigator

The “disableRangeSelector” property allows users to render the period selector without range navigator.

{% tab template= "rangenavigator/periodselector" %}

```typescript

import { RangeNavigator, Chart, IChangedEventArgs, PeriodSelector, AreaSeries, DateTime, PeriodSelectorSettingsModel } from '@syncfusion/ej2-charts';
import { EmitType } from '@syncfusion/ej2-base';

RangeNavigator.Inject(
    PeriodSelector, DateTime, AreaSeries
);
import { chartData } from './datasource.ts';
let periodsValue: PeriodSelectorSettingsModel = {
    periods: [
        { text: '1M', interval: 1, intervalType: 'Months' }, { text: '3M', interval: 3, intervalType: 'Months' },
        { text: '6M', interval: 6, intervalType: 'Months' }, { text: 'YTD' },
        { text: '1Y', interval: 1, intervalType: 'Years' },
        { text: '2Y', interval: 2, intervalType: 'Years', selected: true
         },
        { text: 'All' }
    ]
};
let range: RangeNavigator = new RangeNavigator(
        {
        disableRangeSelector: true,
        valueType: 'DateTime',
        series: [
            {
                dataSource: chartData,
                xName: 'x', yName: 'close', type: 'Area', width: 2,

            }
        ], periodSelectorSettings: periodsValue,
        }, '#element');
```

{% endtab %}

## See Also

* [LightWeight](./lightweight/)