---
title: "Change Size"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Change Size

The different Switch sizes available are default and small. To reduce the size of default Switch to small,
set the [`cssClass`](../../api/switch#cssclass) property to `e-small`.

{% tab template= "switch/size", sourceFiles="app.ts,index.html",
es5Template="text", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Small Switch.
let switchObj: Switch = new Switch({ cssClass: 'e-small' });
switchObj.appendTo('#switch1');

//Default Switch.
switchObj = new Switch({});
switchObj.appendTo('#switch2');
```

{% endtab %}