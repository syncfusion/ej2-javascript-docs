---
title: "Prevent duplicate toast display"
component: "Toast"
description: "This example demonstrates how to prevent the identical same Essential JS 2 Toast is displayed on a screen."
---

# Prevent duplicate toast display

You can prevent identical same toast displaying in a screen by the event function and terminate the toast displaying process by setting the cancel event property in the [beforeOpen](../../api/toast/#beforeopen) event.

The following sample demonstrates preventing duplicate title toast element displaying with custom code blocks.

{% tab template="toast/toast", es5Template="es5_toast_prevDub", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast, ToastModel, ToastBeforeOpenArgs} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toasts: ToastModel[] = [
    { title: 'Warning !', content: 'There was a problem with your network connection.' , isOpen: false},
    { title: 'Success !', content: 'Your message has been sent successfully.' , isOpen: false},
    { title: 'Error !', content: 'A problem has been occurred while submitting your data.' , isOpen: false },
];
let prevDuplicates: boolean = false;
let toastFlag: number = 0;

let toast: Toast = new Toast({
    position: {
        X: 'Center'
    },
    beforeOpen: onBeforeOpen,
    close: onClose,
    created: onCreate
});
toast.appendTo('#element');
++toastFlag;

document.getElementById('show_toast').onclick = () => {
    toast.show(toasts[toastFlag]);
    ++toastFlag;
    if (toastFlag === (toasts.length)) {
        toastFlag = 0;
    }
}

function onBeforeOpen(e: ToastBeforeOpenArgs): void {
    if (preventDuplicate(e)) {
        e.cancel = true;
    }
}

function preventDuplicate(e: ToastBeforeOpenArgs): boolean {
    for (let i: number = 0; i < toasts.length; i++) {
      if (toasts[i].title === e.options.title && !toasts[i].isOpen) {
       toasts[i].isOpen = true;
        return false;
      }
    }
    return true;
}

function onCreate(): void {
    toast.show(toasts[toastFlag]);
    ++toastFlag;
}

function onClose(e: any): void {
    for (let i: number = 0; i < toasts.length; i++) {
        if (toasts[i].title === e.options.title) {
            toasts[i].isOpen = false;
        }
    }
}
```

{% endtab %}