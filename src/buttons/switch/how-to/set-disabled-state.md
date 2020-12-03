---
title: "Set disabled state"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Set disabled state

Switch can be disabled by setting the [`disabled`](../../api/switch#disabled) property to true.

The following example illustrates how to disable support in Switch component.

{% tab template= "switch/getting-started", sourceFiles="app.ts,index.html",
es5Template="disable-template", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Switch component with disabled support.
let switchObj: Switch = new Switch({ disabled: true });

// Render initialized Switch.
switchObj.appendTo('#element');
```

{% endtab %}