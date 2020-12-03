---
title: "Name and Value in form submit"
component: "RadioButton"
description: "TypeScript RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Name and Value in form submit

The [`name`](../../api/radio-button#name) attribute of the RadioButton is used to group RadioButton. When the RadioButton are grouped in form, the checked items [`value`](../../api/radio-button#value) attribute
will be post to server on form submit that can be retrieved through the name. The disabled RadioButton
value will not be sent to the server on form submit.

In the following code snippet, Credit and Debit card is in checked state.
Now, the value that is in checked state will be sent on form submit.

{% tab template= "radio-button/form", sourceFiles="app.ts,index.html,styles.css",
es5Template="form-template" %}

```typescript
import { Button, RadioButton } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Name and Value attribute in form submit.
let radiobutton: RadioButton = new RadioButton({label: 'Credit/Debit Card', name: 'payment', value: 'credit/debit', checked: true});
radiobutton.appendTo('#radiobutton1');

radiobutton = new RadioButton({label: 'Net Banking', name: 'payment', value: 'netbanking'});
radiobutton.appendTo('#radiobutton2');

radiobutton = new RadioButton({label: 'Cash on Delivery', name: 'payment', value: 'cashondelivery'});
radiobutton.appendTo('#radiobutton3');

radiobutton = new RadioButton({label: 'Others', name: 'payment', value: 'others'});
radiobutton.appendTo('#radiobutton4');

let button: Button = new Button({ isPrimary: true });
button.appendTo('#btnElement');

```

{% endtab %}