---
title: "Time out"
component: "Toast"
description: "This section explains how to set time-out value for the Toast component, which is used to display toast till the time-out reaches without user interaction."
---

# Time out

The toast can be expired based on the [timeOut](../api/toast/#timeout) property. The toast can live till the time out reaches without user interaction, a time out value is considered as a millisecond.

* The `timeOut` delay can be visually represented using [Progress Bar](./config/#progress-bar).

* The [extendedTimeOut](../api/toast/#extendedtimeout) property determines how long the toast should be displayed after a user hovers over it.

> You can terminate the process by using the [showCloseButton](../api/toast/#showclosebutton) property for destroying the toast at any time.

{% tab template="toast/timeout", es5Template="es5_toast_timeOut", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple, closest} from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Anjolie Stokes',
    content: '<p><img src="https://ej2.syncfusion.com/vue/demos/src/toast/resource/laura.png"></p>',
    position: { X: "Right", Y: "Bottom" },
    width: 230,
    height: 250,
        buttons : [{
        model: { content: "Ignore" }
    }, {
      model: { content: "reply" }
    }]
});
toast.appendTo('#elementToastTime');
toast.show();

document.getElementById('show_toast').onclick = () => {
  let value = parseInt(document.getElementById('toast_input_index').value)
  toast.show({timeOut: value});
}

```

{% endtab %}

## Static toast

You can prevent auto hiding in a toast as visible like static by setting zero (`0`) value in the timeOut Property.

{% tab template="toast/toast", es5Template="es5_toast_cusTimeOut", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple, closest} from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    showCloseButton: true,
    position: { X: "Right" },
    timeOut: 0
});
toast.appendTo('#element');
toast.show();

document.getElementById('show_toast').onclick = () => {
    toast.show();
}

```

{% endtab %}

## See Also

* [Hide the toast on click](./how-to/close-the-toast-with-click-tap/)