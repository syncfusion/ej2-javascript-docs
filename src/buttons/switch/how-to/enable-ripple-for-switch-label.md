---
title: "Enable ripple for Switch label"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Enable ripple for Switch label

By default, label with ripple effect is not available in Switch. You can achieve this using `rippleMouseHandler`
method.

The following example illustrates how to enable ripple effect for labels in Switch component.

{% tab template= "switch/ripple", sourceFiles="app.ts,index.html,styles.css",
es5Template="ripple", isDefaultActive=true %}

```typescript
import { Switch, rippleMouseHandler } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Switch component.
let switchObj: Switch = new Switch({ checked: true });

// Render initialized Switch.
switchObj.appendTo('#switch1');

// Function to handle ripple effect for Switch with label.
document.querySelector('.lSize label').addEventListener('mouseup', rippleHandler);
document.querySelector('.lSize label').addEventListener('mousedown', rippleHandler);
function rippleHandler(e: MouseEvent): void  {
    let rippleSpan: Element = this.parentElement.nextElementSibling.querySelector('.e-ripple-container');
    if (rippleSpan) {
        rippleMouseHandler(e, rippleSpan);
    }
}
```

{% endtab %}