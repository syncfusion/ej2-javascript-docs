---
title: "Enable RTL"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Enable RTL

Switch component has RTL support. This can be achieved by setting [`enableRtl`](../../api/switch#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in Switch component.

{% tab template= "switch/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Switch component.
let switchObj: Switch = new Switch({ enableRtl: true });

// Render initialized Switch.
switchObj.appendTo('#element');
```

{% endtab %}