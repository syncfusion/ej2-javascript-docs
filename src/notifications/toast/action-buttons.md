---
title: "Action Buttons"
component: "Toast"
description: "The Toast component action button section explains how to add button components inside the toast component using button properties."
---

# Action Buttons

You can include action buttons to the toast control by adding the [buttons](../api/toast#buttons) property. The collection of Essential JS 2 button models can be bound to the `model` property inside the buttons property. You can also include the click event callback function for each button.

{% tab template="toast/actionBtn", es5Template="es5_toast_actionBtn", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple, closest} from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Anjolie Stokes',
    content: 'Thanks for the update!',
    icon: 'e-laura',
    position: { X: "Right", Y: "Bottom" },
    width: 280,
    height: 120,
        buttons : [{
        model: { content: "Ignore" }, click: btnClick
    }, {
      model: { content: "reply" }
    }]
});
toast.appendTo('#elementToastTime');
toast.show();

document.getElementById('show_toast').onclick = () => {
  toast.show();
}

function btnClick(e: Event) {
 let toastEle = closest(e.target, '.e-toast');
 toast.hide(toastEle);
}

```

{% endtab %}

## See Also

* [How to add dynamic template](./how-to/add-dynamic-template/)