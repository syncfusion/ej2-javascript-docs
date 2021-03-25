---
title: "Prevent toast close with mobile swipe"
component: "Toast"
description: "This example demonstrates how to prevent the identical same Essential JS 2 Toast is displayed on a screen."
---

# Prevent toast close with mobile swipe

You can prevent the toast close with mobile swipe action by setting [beforeClose](../../api/toast/#beforeClose) argument cancel value to true while argument type as a swipe. The following code shows how to prevent toast close with mobile swipe.

The following sample demonstrates preventing toast close with mobile swipe element displaying with custom code blocks.

{% tab template="toast/toast", es5Template="es5_toast_prevSwipe", isDefaultActive=true, sourceFiles="index.ts, index.html"  %}

```typescript
import {Toast, ToastBeforeCloseArgs} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    position: { X: "Center" },
    beforeClose: onBeforeClose,
});
toast.appendTo('#element');
toast.show();
function onBeforeClose (args: ToastBeforeCloseArgs) {
        if (args.type === "swipe") {
            args.cancel = true;
        }
    }
document.getElementById('show_toast').onclick = () => {
  toast.show();
}
```

{% endtab %}