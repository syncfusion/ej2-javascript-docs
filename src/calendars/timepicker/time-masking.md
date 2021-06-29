---
title: "Time masking"
component: "TimePicker"
description: "Miscellaneous aspects of customizing the TimePicker"
---

# Enable the Masked Input

The TimePicker has built-in support to masking the time value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the TimePicker.

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

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

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
timepickerPlaceholder.appendTo('#palceholder');
```

{% endtab %}
