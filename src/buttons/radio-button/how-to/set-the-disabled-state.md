---
title: "RadioButton How To sections"
component: "RadioButton"
description: "TypeScript RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Set the disabled state

RadioButton component can be enabled/disabled by giving [`disabled`](../../api/radio-button#disabled) property. To disable RadioButton component,
the `disabled` property can be set as `true`.

The following example illustrates how to disable a radio button and the selected one is displayed using [`change`](../../api/radio-button#change) event.

{% tab template= "radio-button/disabled", sourceFiles="app.ts,index.html,styles.css",
es5Template="disabled-template" %}

```typescript
import { RadioButton, ChangeEventArgs } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize RadioButton component.
let radiobutton: RadioButton = new RadioButton({ label: 'Option 1', name: 'default', checked: true, change: onChange });

// Render initialized RadioButton.
radiobutton.appendTo('#element1');

radiobutton = new RadioButton({ label: 'Option 2', name: 'default', disabled: true, change: onChange });
radiobutton.appendTo('#element2');

radiobutton = new RadioButton({ label: 'Option 3', name: 'default', change: onChange });
radiobutton.appendTo('#element3');

function onChange(args: ChangeEventArgs): void {
   document.getElementById('text').innerText = 'Selected : ' + this.label;
}

```

{% endtab %}