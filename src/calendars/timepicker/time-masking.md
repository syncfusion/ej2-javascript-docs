---
title: "Time masking"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the TimePicker"
---

# Enable the Masked Input

TimePicker has `enableMask` property that provides the option to enable the built-in date masking support. Also, you must inject the MaskedDateTime module to enable the masking support.

{% tab template="datepicker/mask-module" , sourceFiles="app.ts,index.html",
es5Template="mask-module-template" %}

```typescript

import { TimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
TimePicker.Inject(MaskedDateTime);

let timepickerObject: TimePicker = new TimePicker({
    enableMask: true
});
timepickerObject.appendTo('#mask');
```

{% endtab %}

The mask pattern is defined based on the provided time format to the component. If the format is not specified, the mask pattern is formed based on the default format of the current culture.

| **Keys** | **Actions** |
| --- | --- |
| <kbd>Up / Down arrows</kbd> | To increment and decrement the selected portion of the time. |
| <kbd>Left / Right arrows and Tab</kbd> | To navigate the selection from one portion to next portion |

The following example demonstrates default and custom format of TimePicker component with mask module.

{% tab template="timepicker/mask-support" , sourceFiles="app.ts,index.html",
es5Template="mask-support-template" %}

```typescript

import { TimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
TimePicker.Inject(MaskedDateTime);

let timepickerObject: TimePicker = new TimePicker({
    enableMask: true
});
timepickerObject.appendTo('#mask');

let timepickerFormat: TimePicker = new TimePicker({
    enableMask: true,
    format: "h:mm a",
});
timepickerFormat.appendTo('#format');
```

{% endtab %}

# Configure Mask Placeholder

You can change mask placeholder value through property `maskPlaceholder`. By default , it takes the full name of  time co-ordinates such as `hour`, `minute` and `second`.

While changing to a culture other than `English`, ensure that locale text for the concerned culture is loaded through load method of L10n class for mask placeholder values like below.

```typescript
//Load the L10n from ej2-base
import { L10n } from '@syncfusion/ej2-base';

//load the locale object to set the localized placeholder value
L10n.load({
'de': {
    'timepicker': { hour: 'Stunde' ,minute: 'Minute', second:'Sekunde' }
}
});

```

The following example demonstrates default and customized mask placeholder value.

{% tab template="timepicker/mask-placeholder" , sourceFiles="app.ts,index.html",
es5Template="mask-placeholder-template" %}

```typescript

import { TimePicker, MaskedDateTime } from '@syncfusion/ej2-calendars';
TimePicker.Inject(MaskedDateTime);

let timepickerObject: TimePicker = new TimePicker({
    enableMask: true
});
timepickerObject.appendTo('#mask');

let timepickerPlaceholder: TimePicker = new TimePicker({
    enableMask: true,
    maskPlaceholder: {hour: 'h', minute: 'm', second: 's'}
});
timepickerPlaceholder.appendTo('#placeholder');
```

{% endtab %}
