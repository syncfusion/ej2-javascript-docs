---
title: "Customized CheckBox"
component: "CheckBox"
description: "TypeScript CheckBox how to section, name and value in form submit, and customization of CheckBox appearance, frame & check icon."
---

# Customized CheckBox

## Customize CheckBox Appearance

You can customize the appearance of the CheckBox component using the CSS rules.
Define own CSS rules according to your requirement and assign the class name to the [`cssClass`](../../api/check-box#cssclass) property.

The background and border color of the CheckBox is customized through the custom classes to create primary, success, warning, and danger info type of checkbox.

{% tab template= "check-box/howto", sourceFiles="app.ts,index.html,styles.css",
es5Template="customize-template" %}

```typescript
import { CheckBox, Button } from '@syncfusion/ej2-buttons';

// To customize CheckBox appearance
// Refer the 'e-primary' class details in 'style.css'.
let checkbox: CheckBox = new CheckBox({ label: 'Primary', cssClass: 'e-primary', checked: true });
checkbox.appendTo('#checkbox1');

// Refer the 'e-success' class details in 'style.css'.
checkbox = new CheckBox({ label: 'Success', cssClass: 'e-success', checked: true });
checkbox.appendTo('#checkbox2');

// Refer the 'e-info' class details in 'style.css'.
checkbox = new CheckBox({ label: 'Info', cssClass: 'e-info', checked: true });
checkbox.appendTo('#checkbox3');

// Refer the 'e-warning' class details in 'style.css'.
checkbox = new CheckBox({ label: 'Warning', cssClass: 'e-warning', checked: true });
checkbox.appendTo('#checkbox4');

// Refer the 'e-danger' class details in 'style.css'.
checkbox = new CheckBox({ label: 'Danger', cssClass: 'e-danger', checked: true });
checkbox.appendTo('#checkbox5');

```

{% endtab %}

## Custom Frame

CheckBox frame can be customized as per the requirement by adding CSS rules.

In the following example, to-do list is displayed with round checkbox by changing
`border-radius` as `100%` by adding `e-custom` class.

{% tab template= "check-box/customframe", sourceFiles="app.ts,index.html,styles.css",
es5Template="customframe-template" %}

```typescript
import { CheckBox, Button } from '@syncfusion/ej2-buttons';

// To customize CheckBox frame appearance
let checkbox: CheckBox = new CheckBox({ label: 'Buy Groceries', cssClass: 'e-custom' ,checked: true });
checkbox.appendTo('#checkbox1');

checkbox = new CheckBox({ label: 'Pay Rent', cssClass: 'e-custom' });
checkbox.appendTo('#checkbox2');

checkbox = new CheckBox({ label: 'Make Dinner', cssClass: 'e-custom' });
checkbox.appendTo('#checkbox3');

checkbox = new CheckBox({ label: 'Finish To-do List Article', cssClass: 'e-custom' });
checkbox.appendTo('#checkbox4');

```

{% endtab %}

## Custom Check Icon

CheckBox check icon can be customized as per the requirement by adding CSS rules.

In the following example, the check icon can be customized by changing check icon content, background and
border color in focus and hovered states by adding `e-checkicon` class.

{% tab template= "check-box/custom-icon", sourceFiles="app.ts,index.html,styles.css",
es5Template="customicon-template" %}

```typescript
import { CheckBox, Button } from '@syncfusion/ej2-buttons';

// To customize CheckBox frame appearance
let checkbox: CheckBox = new CheckBox({ label: 'Buy Groceries', cssClass: 'e-checkicon' ,checked: true });
checkbox.appendTo('#checkbox1');

checkbox = new CheckBox({ label: 'Pay Rent', cssClass: 'e-checkicon' });
checkbox.appendTo('#checkbox2');

checkbox = new CheckBox({ label: 'Make Dinner', cssClass: 'e-checkicon' });
checkbox.appendTo('#checkbox3');

checkbox = new CheckBox({ label: 'Finish To-do List Article', cssClass: 'e-checkicon' });
checkbox.appendTo('#checkbox4');

```

{% endtab %}