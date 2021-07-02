---
title: "Date Masking"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Enable the Masked Input

DatePicker has `enableMask` property that provides the option to enable the built-in date masking support. Also, you must inject the MaskedDateTime module to enable the masking support.

{% tab template="datepicker/mask-module" , sourceFiles="app.ts,index.html",
es5Template="mask-module-template" %}

```typescript

import { DatePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DatePicker.Inject(MaskedDateTime);

let datepickerObject: DatePicker = new DatePicker({
    enableMask: true
});
datepickerObject.appendTo('#mask');
```

{% endtab %}

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

| **Keys** | **Actions** |
| --- | --- |
| <kbd>Up / Down arrows</kbd> | To increment and decrement the selected portion of the date. |
| <kbd>Left / Right arrows and Tab</kbd> | To navigate the selection from one portion to next portion |

The following example demonstrates default and custom format of DatePicker component with mask.

{% tab template="datepicker/mask-support" , sourceFiles="app.ts,index.html",
es5Template="mask-support-template" %}

```typescript

import { DatePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DatePicker.Inject(MaskedDateTime);

let datepickerObject: DatePicker = new DatePicker({
    enableMask: true
});
datepickerObject.appendTo('#mask');

let datepickerFormat: DatePicker = new DatePicker({
    enableMask: true,
    format: "M/d/yyyy",
});
datepickerFormat.appendTo('#format');
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of date and time co-ordinates such as `day`, `month`, `year`, `hour` etc.

While changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through load method of L10n class for mask placeholder values like below.

```typescript
//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized mask placeholder value
L10n.load({
'de': {
    'datepicker': { day: 'Tag' , month: 'Monat', year: 'Jahr' }
}
});

```

The following example demonstrates default and customized mask placeholder value.

{% tab template="datepicker/mask-placeholder" , sourceFiles="app.ts,index.html",
es5Template="mask-placeholder-template" %}

```typescript

import { DatePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DatePicker.Inject(MaskedDateTime);

let datepickerObject: DatePicker = new DatePicker({
    enableMask: true
});
datepickerObject.appendTo('#mask');

let datepickerPlaceholder: DatePicker = new DatePicker({
    enableMask: true,
    maskPlaceholder: {day: 'd', month: 'M', year: 'y'}
});
datepickerPlaceholder.appendTo('#placeholder');
```

{% endtab %}
