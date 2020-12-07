---
title: "Template"
component: "Toast"
description: "The Essential JS 2 Toast component template section explains how to customize the toast component as needed."
---

# Template

The Template property in toast can be defined as `HTML element`, this can be either a `string` or `selector`.

The HTML element tag can be given as a string for the [Template](../api/toast/#template) property.

```typescript
template: "<div>Toast Content</div>"

```

The Template property allows getting the template content using the query `selector`. Here, the element 'ID' attribute is specified in the template.

```typescript
template: "#Template"

```

{% tab template="toast/template", es5Template="es5_toast_template", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import { Toast, ToastOpenArgs, ToastCloseArgs, ToastBeforeOpenArgs } from '@syncfusion/ej2-notifications';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { compile, Browser, closest } from '@syncfusion/ej2-base';

let toast: Toast = new Toast({
  template: document.getElementById('template_toast_ele').innerHTML,
  position:  { X: 'Right', Y: 'Bottom' },
  target: document.body,
  extendedTimeout: 0,
  timeOut: 120000
});
toast.appendTo('#element');
toast.show();

let btnEle: HTMLElement = document.getElementById('toast_mail_remainder');
let snoozeFlag: boolean = false;

document.getElementById('show_toast').onclick = () => {
    toast.show();
}

```

{% endtab %}

## See Also

* [How to add dynamic template](./how-to/add-dynamic-template/)
* [How to play an audio before open the toast](./how-to/play-an-audio-before-open-the-toast/)