---
title: "Date Masking"
component: "DatePicker"
description: "Miscellaneous aspects of customizing the date picker"
---

# Enable the Masked Input

The DatePicker has built-in support to masking the date value, when `enableMask` property set as `true`.

To use mask support, inject the MaskedDateTime module in the DatePicker.

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

The selected portions of date and time co-ordinates  can  be incremented and decremented using the Up/Down arrow keys. You can also use Right/Left arrow keys to navigate from one segment to another.

The following example demonstrates default and custom format of DatePicker component with mask module.

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
datepickerPlaceholder.appendTo('#palceholder');
```

{% endtab %}
