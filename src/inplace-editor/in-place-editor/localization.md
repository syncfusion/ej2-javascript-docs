---
title: "Globalization"
component: "In-place Editor"
description: "Learn how to apply localization (l10n), internationalization (i18n), and right-to-left (RTL) format in the Essential JS 2 In-place Editor control."
---

# Globalization

## Localization

Localization library allows you to localize the default text content of the In-place Editor to different cultures using the [locale](../api/inplace-editor/#locale) property. In-place Editor following keys will be localize based on culture.

| Locale key | en-US (default) |
|------|------|
| save | Close |
| cancel | Cancel |
| loadingText | Loading... |
| editIcon | Click to edit |
| editAreaClick | Click to edit |
| editAreaDoubleClick | Double click to edit |

To load translation object in an application use `load` function of `L10n` class. In the following sample, `French` culture is set to In-place Editor and change the tooltip text.

{% tab template="in-place-editor/editable-on", es5Template="es5_locale", sourceFiles="index.ts,index.html" %}

```typescript
import { L10n } from '@syncfusion/ej2-base';
import { InPlaceEditor, EditableType } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

L10n.load({
    'fr-BE': {
        'inplace-editor': {
            'save': 'enregistrer',
            'cancel': 'Annuler',
            'loadingText': 'Chargement...',
            'editIcon': 'Cliquez pour éditer',
            'editAreaClick': 'Cliquez pour éditer',
            'editAreaDoubleClick': 'Double-cliquez pour éditer'
        }
    }
});

let editableOnData: string[] = ['Click', 'DblClick', 'EditIconClick'];

let dropDownObj: DropDownList = new DropDownList({
    dataSource: editableOnData,
    width: 'auto',
    value: 'Click',
    change: onChange,
    placeholder: 'Select edit type'
});
dropDownObj.appendTo('#dropDown');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    locale: 'fr-BE',
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    let editType: EditableType = e.itemData.value as EditableType;
    editObj.editableOn = editType;
    editObj.dataBind();
}
```

{% endtab %}

## Right to left

Specifies the direction of the In-place Editor control using the enableRtl property. For writing systems that require it like Arabic, Hebrew, etc., the direction can be switched to right-to-left.

> It will not change based on the locale property.

{% tab template="in-place-editor/default", es5Template="es5_rtl", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    enableRtl: true
});
editObj.appendTo('#element');
```

{% endtab %}

## Format

Formatting is a way of representing the value in different format. You can format the following mentioned controls with its `format` property, when it passed through the In-place Editor [model](../api/inplace-editor/#model) property.

* [DatePicker](../datepicker/date-format/)
* [DateRangePicker](../daterangepicker/globalization/#customize-the-date-format)
* [DateTimePicker](../api/datetimepicker/#format)
* [NumericTextBox](../numerictextbox/formats/#custom-formats)
* [Slider](../slider/format/)
* [TimePicker](../api/timepicker#format)

{% tab template="in-place-editor/format", es5Template="es5_format", sourceFiles="index.ts,index.html" %}

```typescript

import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';

let editObj: InPlaceEditor = new InPlaceEditor({
    type: 'Date',
    value: new Date('11/23/2018'),
    model: {
        placeholder: 'Select date',
        format: 'yyyy-MM-dd'
    }
});
editObj.appendTo('#element');
```

{% endtab %}