---
title: "Right-To-Left"
component: "CheckBox"
description: "TypeScript CheckBox how to section, name and value in form submit, and customization of CheckBox appearance, frame & check icon."
---

# Right-To-Left

CheckBox component has RTL support. This can be achieved by setting [`enableRtl`](../../api/check-box#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in CheckBox component.

{% tab template= "check-box/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template" %}

```typescript
import { CheckBox } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize CheckBox component.
let checkbox: CheckBox = new CheckBox({ label: 'Default', enableRtl: true });

// Render initialized CheckBox.
checkbox.appendTo('#element');
```

{% endtab %}
