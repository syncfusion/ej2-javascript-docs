---
title: "Configuring Options"
component: "Toast"
description: "The Toast component configuration section explains how to customize the appearance of the Toast component using built-in APIs."
---

# Configuring Options

This section explains the steps required to customize the appearance of the toast using built-in APIs.

## Title and content template

Toast can be created with the notification message. The message contains [title](../api/toast/#title) and [content](../api/toast/#content) of the toasts. The title and contents are adaptable in any resolution.

> The Title or Content property can be given as HTML element/element ID to a string that can be displayed as a toast.

{% tab template="toast/toast", es5Template="es5_toast_default", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    position: { X: "Center" }
});
toast.appendTo('#element');
toast.show();

document.getElementById('show_toast').onclick = () => {
  toast.show();
}

```

{% endtab %}

## Specifying custom target

By default, the toast can be rendered in the document body. You can change the target position for toast rendering using the [target](../api/toast/#target) property. Based on the target, the [position](../api/toast/#position) will be updated.

## Close button

By default, the [showCloseButton](../api/toast/#showclosebutton) is not enabled. You can enable it by setting the true value. Before expiring the toast, you can use this button to close or destroy toasts manually.

## Progress bar

By default, the [showProgressBar](../api/toast/#showprogressbar) is not enabled. If it is enabled, it can visually indicate how long to get toast expires. Based on the [timeOut](../api/toast/#timeout) property, progress bar will appear.

## Newest on top

By default, the newly created toasts will append next with existing toasts. You can change the sequence like inserting before the toast by enabling the [newestOnTop](../api/toast/#newestontop).

Here, The following sample demonstrates the combination of the `target`, `showCloseButton`, `showProgressBar`, and `newestOnTop` properties in toast.

{% tab template="toast/toast_target", es5Template="es5_toast_config", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'File Downloading',
    content: '<div class="progress"><span style="width: 80%"></span></div>',
    showCloseButton: true,
    target: '#toast_target',
    position: { X: "Center" }
    newestOnTop: true,
    showProgressBar: true
});
toast.appendTo('#element');
toast.show();

document.getElementById('show_toast').onclick = () => {
  toast.show();
}
```

{% endtab %}

## Width and height

The dimensions of the toast can be set using the [width](../api/toast/#width) and [height](../api/toast/#height) properties. This will individually set all toasts. You can create different custom dimension toasts.

By default, the toast can be rendered with `300px` width with `auto` height.

> In mobile devices, the default width of the toast gets '100%' width of the page.
> When you set toast width as '100%', the toast occupies full width and will be displayed at the top or bottom based on the position `Y` property.

Both the width and height properties allow setting pixels/numbers/percentage. The number value is considered as pixels.

{% tab template="toast/full_width", es5Template="es5_toast_widHeight", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';
import { RadioButton, ChangeEventArgs as CheckBoxChange, CheckBox, ChangeEventArgs} from '@syncfusion/ej2-buttons';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    position: { X: "Center", Y: "Bottom" },
    width: 400,
    height: 150,
});
toast.appendTo('#element');
toast.show();

let timeDelay = 500;
let radioButton: RadioButton = new RadioButton({ label: 'Top', name: 'toast', value: 'Target', change: checkboxChange });
radioButton.appendTo('#topAlign');

let radioButton2 = new RadioButton({ label: 'Bottom', name: 'toast', value: 'Global', checked: true, change: checkboxChange1 });
radioButton2.appendTo('#bottomAlign');

let checkBoxObj: CheckBox = new CheckBox({ label: '100% Width', change: onChange });
checkBoxObj.appendTo('#fullWidth');

function onChange(e: ChangeEventArgs): void {
  if (e.checked) {
    toast.hide();
    toast.width = "100%";
    toast.title="";
    toast.content="<div class='e-custom'>Take a look at our next generation <b>Javascript</b> <a href='https://ej2.syncfusion.com/home/index.html' target='_blank'>LEARN MORE</a></div>";
    toastShow(timeDelay);
  } else {
    toast.hide();
    toast.width= 300;
    toast.title= 'Matt sent you a friend request',
    toast.content='You have a new friend request yet to accept',
    toastShow(timeDelay);
  }
}

function checkboxChange(e: CheckBoxChange): void {
    if (e.event.target.checked) {
      toast.position.Y = "Top";
      toast.hide();
      toastShow(timeDelay);
    }
}

function checkboxChange1(e: CheckBoxChange): void {
    if (e.event.target.checked) {
      toast.position.Y = "Bottom";
      toast.hide();
      toastShow(timeDelay);
    }
}

function toastShow(timeOutDelay: number): void {
  setTimeout(
    () => {
        toast.show();
    }, timeOutDelay);
}

document.getElementById('show_toast').onclick = () => {
  toast.show();
}
```

{% endtab %}

## See Also

* [Prevent duplicate toasts](./how-to/prevent-duplicate-toast-display/)
* [Customize the progress bar](./how-to/customize-progress-bar-theme-and-sizing/)