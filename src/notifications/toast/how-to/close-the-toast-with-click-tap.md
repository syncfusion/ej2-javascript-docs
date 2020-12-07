---
title: "Close the toast with click/tap"
component: "Toast"
description: "This example demonstrates how to close the Essential JS 2 Toaster component with a click or tap operation."
---

# Close the toast with click/tap

By default, the toasts are expired based on the timeOut value. You can customize the toast hiding process with click/tap action by setting the event args in the [clicked](../../api/toast/toastClickEventArgs/#clicktoclose) callback function with [static Toast](../timeout/#static-toast).

{% tab template="toast/toast", es5Template="es5_toast_click", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastClickEventArgs } from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toast: Toast = new Toast({
  title: 'Matt sent you a friend request',
  content: 'You have a new friend request yet to accept',
  timeOut: 0,
  position: { X: 'Right', Y: 'Bottom' }
  click: onClick
});
toast.appendTo('#element');
toast.show();

document.getElementById('show_toast').onclick = () => {
  toast.show();
}

function onClick(e: ToastClickEventArgs ): void {
  e.clickToClose = true;
}
```

{% endtab %}