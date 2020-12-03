---
title: "Customize RadioButton Appearance"
component: "RadioButton"
description: "TypeScript RadioButton how to section, name and value in form submit, customize RadioButton appearance."
---

# Customize RadioButton Appearance

You can customize the appearance of the RadioButton component by using the CSS rules.
Define own CSS rules according to your requirement and assign the class name to the [`cssClass`](../../api/radio-button#cssclass) property.

The background and border color of the RadioButton is customized through the custom classes to create the primary, success, info, warning, and danger type of RadioButton.

{% tab template= "radio-button/howto", sourceFiles="app.ts,index.html,styles.css",
es5Template="customize-template", isDefaultActive=true %}

```typescript
import { RadioButton } from '@syncfusion/ej2-buttons';

// To customize RadioButton appearance
// Refer the 'e-primary' class details in 'style.css'.
let radiobutton: RadioButton = new RadioButton({ label: 'Primary', name: 'custom', cssClass: 'e-primary' });
radiobutton.appendTo('#radiobutton1');

// Refer the 'e-success' class details in 'style.css'.
radiobutton = new RadioButton({ label: 'Success', name: 'custom', cssClass: 'e-success' });
radiobutton.appendTo('#radiobutton2');

// Refer the 'e-info' class details in 'style.css'.
radiobutton = new RadioButton({ label: 'Info', name: 'custom', cssClass: 'e-info', checked: true });
radiobutton.appendTo('#radiobutton3');

// Refer the 'e-warning' class details in 'style.css'.
radiobutton = new RadioButton({ label: 'Warning', name: 'custom', cssClass: 'e-warning' });
radiobutton.appendTo('#radiobutton4');

// Refer the 'e-danger' class details in 'style.css'.
radiobutton = new RadioButton({ label: 'Danger', name: 'custom', cssClass: 'e-danger' });
radiobutton.appendTo('#radiobutton5');
```

{% endtab %}