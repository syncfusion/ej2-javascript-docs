---
title: "RadioButton Label and Size"
component: "RadioButton"
description: "TypeScript RadioButton component supports different sizes and label."
---

# Label and Size

This section explains the different sizes and labels.

## Label

RadioButton caption can be defined by using the [`label`](../api/radio-button#label) property.
This reduces the manual addition of label for RadioButton. You can customize the label position before or after the RadioButton
through the [`labelPosition`](../api/radio-button#labelposition) property.

{% tab template= "radio-button/label-and-size", sourceFiles="app.ts,index.html,styles.css",
es5Template="label-template",isDefaultActive=true %}

```typescript
import { RadioButton } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Label position - Left.
let radiobutton: RadioButton = new RadioButton({ label: 'Left Side Label', name: 'position', labelPosition: 'Before' });
radiobutton.appendTo('#radiobutton1');

//Label position - Right.
radiobutton = new RadioButton({ label: 'Right Side Label', name: 'position', checked: true });
radiobutton.appendTo('#radiobutton2');
```

{% endtab %}

## Size

The different RadioButton sizes available are default and small. To reduce the size of the default RadioButton to small,
set the [`cssClass`](../api/radio-button#cssclass) property to `e-small`.

{% tab template= "radio-button/label-and-size", sourceFiles="app.ts,index.html,styles.css",
es5Template="size-template" %}

```typescript
import { RadioButton } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Small RadioButton.
let radiobutton: RadioButton = new RadioButton({ label: 'Small', name: 'size', checked: true, cssClass: 'e-small' });
radiobutton.appendTo('#radiobutton1');

//Default RadioButton.
radiobutton = new RadioButton({ label: 'Default', name: 'size' });
radiobutton.appendTo('#radiobutton2');
```

{% endtab %}

## See Also

* [How to customize the RadioButton appearance](./how-to/customize-radiobutton-appearance)
