---
title: "List of controls"
component: "In-place Editor"
description: "Learn supported built-in, injectable controls, and its model configuration for the Essential JS 2 In-place Editor control."
---

# List of controls

In-place Editor renders various controls based on the [type](../api/inplace-editor/inputType/) property and it have built-in and injectable controls. To use injectable controls, inject the required modules into `In-place Editor`. By default, the `type` property set to `Text` and render the `TextBox`.

The following table explains Injectable components module name and built-in components and their types.

| **Injectable Components** | **Built in Components** |
|-----------------------|---------------------|
| [AutoComplete](../auto-complete/)  (`AutoComplete`)        | [TextBox](../textbox/)  (`Text`)             |
| [ComboBox](../combo-box/)  (`ComboBox`)              | [DatePicker](../datepicker/)  (`Date`)        |
| [MultiSelect](../multi-select/)   (`MultiSelect`)        | [DateTimePicker](../datetimepicker/)   (`DateTime`)     |
| [TimePicker](../timepicker/)   (`Time`)         | [DropDownList](../drop-down-list/)  (`DropDownList`)      |
| [DateRangePicker](../daterangepicker/)   (`DateRange`)       | [MaskedTextBox](../maskedtextbox/)   (`Mask`)      |
| [Slider](../slider/)   (`Slider`)             | [NumericTextBox](../numerictextbox/)   (`Numeric`)    |
| [Rte](../rich-text-editor/)     (`RTE`)              |                     |
| [ColorPicker](../color-picker/)    (`Color`)       |                     |

In the following sample, built-in and injectable based In-place Editor controls are rendered.

{% tab template="in-place-editor/controls", es5Template="es5_controls", sourceFiles="index.ts,index.html" %}

```typescript

import { InPlaceEditor, AutoComplete, ColorPicker, ComboBox } from '@syncfusion/ej2-inplace-editor';
import { DateRangePicker, MultiSelect, Rte, Slider, TimePicker } from '@syncfusion/ej2-inplace-editor';

InPlaceEditor.Inject(AutoComplete, ColorPicker, ComboBox, DateRangePicker, MultiSelect, Rte, Slider, TimePicker);

let frameWorkList: string[] = ['Android', 'JavaScript', 'jQuery', 'TypeScript', 'Angular', 'React', 'Vue', 'Ionic'];

let dateObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Date',
    model: {
        placeholder: 'Select date'
    },
    value: new Date('11/23/2018')
});
dateObj.appendTo('#date');

let dateTimeObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DateTime',
    model: {
        placeholder: 'Select date'
    },
    value: new Date('11/23/2018 12:30 PM')
});
dateTimeObj.appendTo('#dateTime');

let dropDownObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DropDownList',
    value: 'Android',
    model: {
        dataSource: frameWorkList,
        placeholder: 'Select frameworks'
    }
});
dropDownObj.appendTo('#dropDowns');

let maskObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Mask',
    value: '123-345-678',
    model: {
        mask: '000-000-000'
    }
});
maskObj.appendTo('#masked');

let numericObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Numeric',
    value: 10,
    model: {
        placeholder: 'Enter number'
    }
});
numericObj.appendTo('#numeric');

let textObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Text',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
textObj.appendTo('#textbox');

let atcObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'AutoComplete',
    value: 'Android',
    model: {
        dataSource: frameWorkList,
        placeholder: 'Select frameworks'
    }
});
atcObj.appendTo('#autoComplete');

let colorObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Color',
    value: '#81aefd'
});
colorObj.appendTo('#color');

let comboBoxObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'ComboBox',
    value: 'Android',
    model: {
        dataSource: frameWorkList,
        placeholder: 'Select frameworks'
    }
});
comboBoxObj.appendTo('#comboBox');

let dateRangeObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DateRange',
    value: [new Date('11/12/2018'), new Date('11/15/2018')],
    model: {
        placeholder: 'Select date'
    }
});
dateRangeObj.appendTo('#dateRange');

let multiSelectObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'MultiSelect',
    value: 'Android',
    model: {
        dataSource: frameWorkList,
        placeholder: 'Select frameworks'
    }
});
multiSelectObj.appendTo('#multiSelect');

let rteObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'RTE',
    value: '<p>Enter your content here</p>',
    model: {
        placeholder: 'Enter your content here'
    }
});
rteObj.appendTo('#rte');

let sliderObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Slider',
    value: 20
});
sliderObj.appendTo('#slider');

let timeObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Time',
    model: {
        placeholder: 'Select date'
    },
    value: new Date('11/23/2018')
});
timeObj.appendTo('#time');

```

{% endtab %}

## Model configuration

Control properties and events can be customized using the In-place Editor [model](../api/inplace-editor/#model) property.

In the following code, the [type](../api/inplace-editor/inputType/) defined as the `Date` and `DatePicker` properties are configured through [model](../api/inplace-editor/#model) property to customize the [DatePicker](../api/datepicker) control at In-place Editor.

```typescript
    model: {
        showTodayButton: true,
        placeholder: 'Select Date'
    }
```

`[src/app/app.ts]`

```typescript

import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';
let editObj: InPlaceEditor = new InPlaceEditor({
    type: 'Date',
    value: new Date('04/12/2018'),
    model: {
        showTodayButton: true,
        placeholder: 'Select Date'
    }
});
editObj.appendTo('#element');

```

## See Also

* [HTML5 components](./integration/)