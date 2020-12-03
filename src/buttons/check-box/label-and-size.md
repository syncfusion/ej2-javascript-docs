---
title: "CheckBox Label and Size"
component: "CheckBox"
description: "TypeScript CheckBox component supports different sizes and label."
---

# Label and Size

This section explains the different sizes and labels.

## Label

The CheckBox caption can be defined by using the [`label`](../api/check-box#label) property.
This reduces the manual addition of label for CheckBox. You can customize the label position before or after the CheckBox
through the [`labelPosition`](../api/check-box#labelposition) property.

{% tab template= "check-box/label-and-size", sourceFiles="app.ts,index.html,styles.css",
es5Template="label-template", isDefaultActive=true %}

```typescript
import { CheckBox } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Label position - Left.
let checkbox: CheckBox = new CheckBox({ label: 'Left Side Label', labelPosition: 'Before' });
checkbox.appendTo('#checkbox1');

//Label position - Right.
checkbox = new CheckBox({ label: 'Right Side Label', checked: true });
checkbox.appendTo('#checkbox2');
```

{% endtab %}

## Size

The different CheckBox sizes available are default and small. To reduce the size of default CheckBox to small,
set the [`cssClass`](../api/check-box#cssclass) property to `e-small`.

{% tab template= "check-box/label-and-size", sourceFiles="app.ts,index.html,styles.css",
es5Template="size-template" %}

```typescript
import { CheckBox } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Small CheckBox.
let checkbox: CheckBox = new CheckBox({ label: 'Small', cssClass: 'e-small' });
checkbox.appendTo('#checkbox1');

//Default CheckBox.
checkbox = new CheckBox({ label: 'Default' });
checkbox.appendTo('#checkbox2');
```

{% endtab %}

## See Also

* [CheckBox customization](./how-to/customized-checkbox)
