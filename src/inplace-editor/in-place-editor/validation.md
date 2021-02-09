---
title: "Validation"
component: "In-place Editor"
description: "Learn how to add rules and to use validation, and then customize the error message in the Essential JS 2 In-place Editor control."
---

# Validation

In-place Editor control supports validation and it can be achieved by adding rules to the [validationRules](../api/inplace-editor/#validationrules) property, its child property `key` must be same as [name](../api/inplace-editor/#name) property, otherwise validation not performed. Submitting data to the server or calling the [validate](../api/inplace-editor/#validate) method validation executed.

## Validation Rules

In-place Editor has following validation rules, which are used to perform validation.

| Rules | Description | Example |
|------|------|------|
| `required` | The input element must have any input values | a or 1 or - |
| `email` | The input element must have valid `email` format values | <inplace@syncfusion.com> |
| `url` | The  input element must have valid `url` format values| <http://syncfusion.com/> |
| `date` | The  input element must have valid `date` format values | 12/25/2019 |
| `dateIso` | The  input element must have valid `dateIso` format values | 2019-12-25 |
| `number` | The  input element must have valid `number` format values | 1.0 or 1 |
| `maxLength` | Input value must have less than or equal to `maxLength` character length | if `maxLength: 5`, [check] is valid and [checking] is invalid |
| `minLength` | Input value must have less than or equal to `minLength` character length | if `minLength: 5`, [testing] is valid and [test] is invalid |
| `rangeLength` | Input value must have value between `rangeLength` character length | if `rangeLength: [4,5]`, [test] is valid and [key] is invalid
| `range` | Input value must have value between `range` number | if `range: [4,5]`, [4] is valid and [6] is invalid |
| `max` | Input value must have less than or equal to `max` number | if `max: 3`, [3] is valid and [4] is invalid |
| `min` | Input value must have less than or equal to `min` number | if `min: 4`, [5] is valid and [2] is invalid |
| `regex` | Input value must have valid `regex` format | if `regex: '^[A-z]+$'`, [a] is valid and [1] is invalid |

## Step by Step validation configuration

The following steps are used to configure validation in In-place Editor.

Step 1: To perform default validation in In-place Editor the `name` property is mandatory. And the specified name must be the same as the key name.

Step 2:  The corresponding name specified in the name property should bind with the `validationRules` property. For example, in the below code snippet, the `Number`  in the name property is bind with the `maxLength`  of validationRules.  Likewise, you can bind with the in-build validation configurations in the above table.

{% tab template="in-place-editor/validation-sample", es5Template="es5_validation_sample", sourceFiles="index.ts,index.html" %}

```typescript

import {
  InPlaceEditor,
  ValidateEventArgs
} from "@syncfusion/ej2-inplace-editor";

let textObj: InPlaceEditor = new InPlaceEditor({
  mode: "Inline",
  type: "Numeric",
  name: "Number",
  model: {
    placeholder: "Select Number"
  },
  validationRules: {
    Number: { maxLength: 5 }
  }
});
textObj.appendTo("#numeric");

```

{% endtab %}

In the following sample, first editor value submitted without select any date, so the default error message will be displayed below the `DatePicker` element. Second editor configured with the [validating](../api/inplace-editor/#validating) event with the handler. In handler event [errorMessage](../api/inplace-editor/validateEventArgs/#errormessage) argument value modified and it will show below the `DatePicker` element.

{% tab template="in-place-editor/validation", es5Template="es5_validation", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ValidateEventArgs } from '@syncfusion/ej2-inplace-editor';

let textObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Date',
    name: 'Today',
    emptyText: 'dd/mm/yyyy',
    model: {
        placeholder: 'Select date'
    },
    validationRules : {
        Today: { required: true }
    }
});
textObj.appendTo('#textBox');

let dateObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'Date',
    name: 'TodayCustom',
    emptyText: 'dd/mm/yyyy',
    model: {
        placeholder: 'Select date'
    },
    validationRules : {
        TodayCustom: { required: true }
    },
    validating: function(e: ValidateEventArgs) {
        e.errorMessage = 'Field should not be empty';
    }
});
dateObj.appendTo('#date');
```

{% endtab %}

* For more details about validation configuration, refer this documentation [section](../api/form-validator).

* For custom validation except specifying validationRules, specify errorMessage at validating event, message will be shown when the value is `Empty`.

## See Also

* [Indication to unsaved value](./how-to/custom-indication)