---
title: "Play an audio before open the toast"
component: "Toast"
description: "This example demonstrates how to play audio in the background while opening the Essential JS 2 Toaster component."
---

# Play an audio before open the toast

The following sample demonstrates how to play an audio in background while opening the toast by including audio play codes into the beforeOpen event function.

> To stop the audio after displaying the toast, use the [open](../../api/toast/#open) event in toast. For further customization, check the Toast Events [APIs](../../api/toast/#events).

{% tab template="toast/audio", es5Template="es5_toast_audio", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    position: { X: 'Right', Y: 'Bottom' }
    beforeOpen: onBeforeOpen
});
toast.appendTo('#element');

document.getElementById('show_toast').onclick = () => {
  toast.show();
}

function onBeforeOpen(e: ToastBeforeOpenArgs): void {
  let audio: HTMLAudioElement = new Audio('https://drive.google.com/uc?export=download&id=1M95VOpto1cQ4FQHzNBaLf0WFQglrtWi7');
  audio.play();
}
```

{% endtab %}
