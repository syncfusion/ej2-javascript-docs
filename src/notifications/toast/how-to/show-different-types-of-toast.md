---
title: "Show different types of toast"
component: "Toast"
description: "This example demonstrates how to create different types of Essential JS 2 Toast component is displayed on a screen."
---

# Show different types of toast

The Essential JS 2 toast has the following predefined styles that can be defined using the [cssClass](../../api/toast/#cssclass) property for achieving different types of toast:

| Class | Description |
| -------- | -------- |
| e-toast-success | Represents a positive toast |
| e-toast-info | Represents an informative toast |
| e-toast-warning | Represents a toast with caution |
| e-toast-danger | Represents a negative toast |

{% tab template="toast/types", es5Template="es5_toast_types", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastModel} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toasts: ToastModel[] = [
  { title: 'Warning !', content: 'There was a problem with your network connection.', cssClass: 'e-toast-warning' },
  { title: 'Success !', content: 'Your message has been sent successfully.', cssClass: 'e-toast-success'},
  { title: 'Error !', content: 'A problem has been occurred while submitting your data.', cssClass: 'e-toast-danger' },
  { title: 'Information !', content: 'Please read the comments carefully.', cssClass: 'e-toast-info' }
];
let toastFlag: number = 0;
let toast: Toast = new Toast({
    position: { X: 'Right', Y: 'Bottom' }
});
toast.appendTo('#element');
toast.show(toasts[toastFlag]);
++toastFlag;

document.getElementById('show_toast').onclick = () => {
  toast.show(toasts[toastFlag]);
  ++toastFlag;
  if (toastFlag === (toasts.length)) {
      toastFlag = 0;
  }
}

```

{% endtab %}