---
title: "Restrict the maximum toast to show"
component: "Toast"
description: "This example demonstrates how to restrict the maximum Essential JS 2 Toast count is displayed on a screen."
---

# Restrict the maximum toast to show

You can restrict the maximum toast count by using the event callback function and terminate the toast displaying process by setting the cancel event property in the [beforeOpen](../../api/toast/#beforeopen) event.

The following sample demonstrates restricting toast displaying up to 3. You can restrict by your own count with custom code blocks.

{% tab template="toast/toast", es5Template="es5_toast_maxCount", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastModel} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let maxCount: number = 3;
let toasts: ToastModel[] = [
    { title: 'Warning !', content: 'There was a problem with your network connection.' },
    { title: 'Success !', content: 'Your message has been sent successfully.' },
    { title: 'Error !', content: 'A problem has been occurred while submitting your data.' },
    { title: 'Information !', content: 'Please read the comments carefully.' }
];
let toastFlag: number = 0;

let toast: Toast = new Toast({
    title: 'Sample Toast Title',
    content: 'Sample Toast content'
    position: { X: 'Right', Y: 'Bottom' }
    beforeOpen: onBeforeOpen
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

function onBeforeOpen(e: ToastBeforeOpenArgs): void {
  if (maxCount === toast.element.childElementCount) {
   e.cancel =true;
  } else {
    e.cancel = false;
  }
}

```

{% endtab %}