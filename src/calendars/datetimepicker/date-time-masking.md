---
title: "Date and Time masking"
component: "DateTimePicker"
description: "Miscellaneous aspects of customizing the datetimepicker"
---

# Enable the Masked Input

DateTimePicker has `enableMask` property that provides the option to enable the built-in date masking support. Also, you must inject the MaskedDateTime module to enable the masking support.

{% tab template="datetimepicker/mask-module" , sourceFiles="app.ts,index.html",
es5Template="mask-module-template" %}

```typescript

import { DateTimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DateTimePicker.Inject(MaskedDateTime);

let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enableMask: true
});
datetimepickerObject.appendTo('#mask');
```

{% endtab %}

The mask pattern is defined based on the provided date format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

| **Keys** | **Actions** |
| --- | --- |
| <kbd>Up / Down arrows</kbd> | To increment and decrement the selected portion of the date and time. |
| <kbd>Left / Right arrows and Tab</kbd> | To navigate the selection from one portion to next portion |

The following example demonstrates default and custom format of DateTimePicker component with mask.

{% tab template="datetimepicker/mask-support" , sourceFiles="app.ts,index.html",
es5Template="mask-support-template" %}

```typescript

import { DateTimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DateTimePicker.Inject(MaskedDateTime);

let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enableMask: true
});
datetimepickerObject.appendTo('#mask');

let datetimepickerFormat: DateTimePicker = new DateTimePicker({
    enableMask: true,
    format: "M/d/yyyy hh:mm a",
});
datetimepickerFormat.appendTo('#format');
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
    'datetimepicker': { day: 'Tag' , month: 'Monat', year: 'Jahr', hour: 'Stunde' ,minute: 'Minute', second:'Sekunden' }
}
});

```

The following example demonstrates default and customized mask placeholder value.

{% tab template="datetimepicker/mask-placeholder" , sourceFiles="app.ts,index.html",
es5Template="mask-placeholder-template" %}

```typescript

import { DateTimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
DateTimePicker.Inject(MaskedDateTime);

let datetimepickerObject: DateTimePicker = new DateTimePicker({
    enableMask: true
});
datetimepickerObject.appendTo('#mask');

let datetimePlaceholder: DateTimePicker = new DateTimePicker({
     enableMask: true,
    maskPlaceholder: {day: 'd', month: 'M', year: 'y', hour: 'h', minute: 'm', second: 's'}
});
datetimePlaceholder.appendTo('#placeholder');
```

{% endtab %}
