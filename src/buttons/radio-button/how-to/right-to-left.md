---
title: "Right-To-Left"
component: "RadioButton"
description: "TypeScript RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Right-To-Left

RadioButton component has RTL support. This can be achieved by setting [`enableRtl`](../../api/radio-button#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in RadioButton component.

{% tab template= "radio-button/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template" %}

```typescript
import { RadioButton } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize RadioButton component.
let radiobutton: RadioButton = new RadioButton({ label: 'Option 1', name: 'default', enableRtl: true });

// Render initialized RadioButton.
radiobutton.appendTo('#element1');

radiobutton = new RadioButton({ label: 'Option 2', name: 'default', enableRtl: true, checked: true });
radiobutton.appendTo('#element2');
```

{% endtab %}