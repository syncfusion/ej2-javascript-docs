---
title: "Submit name and value in form"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Submit name and value in form

The [`name`](../../api/switch#name) attribute of the Switch is used to group Switches. When the Switches are grouped in form, the checked items [`value`](../../api/switch#value) attribute will post to the server on form submit. The disabled and unchecked Switch values will not be sent to the server on form submit.

In the following code snippet, USB and Wi-Fi in the [`checked`](../../api/switch#checked) state, and Bluetooth is in disabled state. Values that are in checked state only be sent on form submit.

{% tab template= "switch/form", sourceFiles="app.ts,index.html,styles.css",
es5Template="form-template", isDefaultActive=true %}

```typescript
import { Switch, Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Name and Value attribute in form submit.
let switchObj: Switch = new Switch({ name: 'Tethering',  value: 'USB', checked: true });
switchObj.appendTo('#switch1');

switchObj = new Switch({ name: 'Hotspot',  value: 'Wi-Fi', checked: true });
switchObj.appendTo('#switch2');

switchObj = new Switch({ name: 'Tethering',  value: 'Bluetooth', disabled: true });
switchObj.appendTo('#switch3');

let button: Button = new Button({ isPrimary: true });
button.appendTo('#btnElement');

```

{% endtab %}
