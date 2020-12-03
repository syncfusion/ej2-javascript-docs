---
title: "Name and Value in form submit"
component: "CheckBox"
description: "TypeScript CheckBox how to section, name and value in form submit, and customization of CheckBox appearance, frame & check icon."
---

# Name and Value in form submit

The [`name`](../../api/check-box/#name) attribute of the CheckBox is used to group Checkboxes. When the Checkboxes are grouped in form, the checked items [`value`](../../api/check-box/#value) attribute
will post to the server on form submit that can be retrieved through the name. The disabled and unchecked CheckBox
value will not be sent to the server on form submit.

In the following code snippet, Cricket and Hockey are in the checked state, Tennis is in [`disabled`](../../api/switch/#disabled) state and Basketball is in unchecked state.
Now, the value that is in checked state only be sent on form submit.

{% tab template= "check-box/form", sourceFiles="app.ts,index.html,styles.css",
es5Template="form-template", isDefaultActive=true %}

```typescript
import { CheckBox, Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Name and Value attribute in form submit.
let checkbox: CheckBox = new CheckBox({ name: 'Sport',  value: 'Cricket', label: 'Cricket', checked: true });
checkbox.appendTo('#checkbox1');

checkbox = new CheckBox({ name: 'Sport',  value: 'Hockey', label: 'Hockey', checked: true });
checkbox.appendTo('#checkbox2');

checkbox = new CheckBox({ name: 'Sport',  value: 'Tennis', label: 'Tennis', disabled: true });
checkbox.appendTo('#checkbox3');

checkbox = new CheckBox({ name: 'Sport',  value: 'Basketball', label: 'Basketball' });
checkbox.appendTo('#checkbox4');

let button: Button = new Button({ isPrimary: true });
button.appendTo('#btnElement');

```

{% endtab %}