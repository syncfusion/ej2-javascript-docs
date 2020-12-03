---
title: "Toggle between the states"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit, toggle between the states."
---

# Change switch state using toggle method

This section explains about how to toggle between the switch states using [`toggle`](../../api/switch/#toggle) method.

{% tab template= "switch/text", sourceFiles="app.ts,index.html",
es5Template="toggle", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';

//Set text in switch toggle states.
let switchObj: Switch = new Switch({ onLabel: 'ON', offLabel: 'OFF' });
switchObj.appendTo('#switch1');

switchObj.toggle();
```

{% endtab %}

> Switch triggers [`change`](../../api/switch/#change) event on every state stage to perform custom operations.