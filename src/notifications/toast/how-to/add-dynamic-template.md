---
title: "Add dynamic template"
component: "Toast"
description: "This example demonstrates how to dynamically change a template for display in multiple Essential JS 2 Toaster component."
---

# Add dynamic template

Toast supports to change templates dynamically with displaying in multiple toasts. You can change the toast properties while calling in the [show](../../api/toast/#show) method.

{% tab template="toast/toast", es5Template="es5_toast_dynamic_tempate", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastClickEventArgs } from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toast: Toast = new Toast({
    position: { X: 'Right', Y: 'Bottom' }
    click: onClick
});

let toastFlag: number = 0;
let toasts = [ { template: '2 Mail has received'},{ template: 'User Guest Logged in'},{ template: 'Logging in as Guest'},{ template: 'Ticket has reserved '},{ template: '#templateToast' }];

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

function onClick(e: ToastClickEventArgs ): void {
  e.clickToClose = true;
}
```

{% endtab %}