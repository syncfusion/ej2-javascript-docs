---
title: "Show multiple toasts in various positions"
component: "Toast"
description: "This example demonstrates how to create multiple Essential JS 2 Toast component in various position on the screen."
---

# Show multiple toasts in various positions

By default, the positions of the new toasts are only updated after the visible toasts have been destroyed. If You need to display multiple toasts with different positions, initiate another toasts.

The following sample demonstrates adding multiple toasts in different positions.

{% tab template="toast/toast-position", es5Template="es5_toast_multiPos", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastClickEventArgs } from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toast: Toast = new Toast({
    title: 'Warning !',
    content: 'There was a problem with your network connection.'
    position: { X: 'Right', Y: 'Bottom' }
    click: onClick
});
toast.appendTo('#element');
toast.show();

let toast1: Toast = new Toast({
    title: 'Success !',
    content: 'Your message has been sent successfully.'
    position: { X: 'Left', Y: 'Bottom' }
    click: onClick
});
toast1.appendTo('#element1');
toast1.show();

document.getElementById('show_toast').onclick = () => {
  toast.show();
}

document.getElementById('show_toast1').onclick = () => {
  toast1.show();
}

function onClick(e: ToastClickEventArgs ): void {
  e.clickToClose = true;
}
```

{% endtab %}