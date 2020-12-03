---
title: "Customize the appearance of a Switch"
component: "Switch"
description: "TypeScript Switch how to section, customization of Switch bar and handle, change size, name and value in form submit."
---

# Customize the appearance of a Switch

You can customize the appearance of the Switch component using the CSS rules. Define your own CSS rules according to your requirement and assign the class name to the [`cssClass`](../../api/switch#cssClass) property.

## Customize Switch bar and handle

Switch bar and handle can be customized as per requirement using CSS rules. Switch bar and handle customized using `cssClass` property. In the following sample, the `border-radius` CSS property for the Switch bar (`e-switch-inner`) and handle (`e-switch-handle`) elements was changed border radius circle to square shape.

{% tab template= "switch/customize", sourceFiles="app.ts,index.html,styles.css",
es5Template="customize-template", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';

// Initialize Switch with square cssClass.
let switchObj: Switch = new Switch({ cssClass: 'square' });
switchObj.appendTo('#switch1');

// Initialize Switch with custom-switch cssClass.
switchObj = new Switch({ cssClass: 'custom-switch', checked: true });
switchObj.appendTo('#switch2');

// Initialize Switch with handle-text cssClass.
switchObj = new Switch({ cssClass: 'handle-text' });
switchObj.appendTo('#switch3');

```

{% endtab %}

## Color the Switch

Switch colors can be customized as per the requirement using CSS rules. Switch bar and handle colors customized using [`cssClass`](../../api/switch/#cssclass) property. In the following sample, the Switch bar (`e-switch-inner`) element background and border colors were changed from default colors.

{% tab template= "switch/customize-color", sourceFiles="app.ts,index.html,styles.css",
es5Template="customize-template", isDefaultActive=true %}

```typescript
import { Switch } from '@syncfusion/ej2-buttons';

// Initialize Switch with bar-color cssClass.
let switchObj: Switch = new Switch({ cssClass: 'bar-color' });
switchObj.appendTo('#switch1');

// Initialize Switch with handle-color cssClass.
switchObj = new Switch({ cssClass: 'handle-color', checked: true });
switchObj.appendTo('#switch2');

// Initialize Switch with custom-iOS cssClass.
switchObj = new Switch({ cssClass: 'custom-iOS', checked: true });
switchObj.appendTo('#switch3');
```

{% endtab %}