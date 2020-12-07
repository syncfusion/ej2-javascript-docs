---
title: "Animations"
component: "Toast"
description: "The Toast component supports custom animations for both show and hide actions by providing an animation option."
---

# Animations

The toast control supports custom animations for both shows and hide actions from the provided animation option of the `Animation` library.

The default animation is given as `FadeIn` for showing the toast and `FadeOut` for hiding the toast.

The following sample demonstrates some types of animations that suit toast. You can check all the animation effects here.

{% tab template="toast/animation", es5Template="es5_toast_animation", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript

import {Toast} from '@syncfusion/ej2-notifications';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { enableRipple, Effect } from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    position: { X: 'Right', Y: 'Bottom' }
});
toast.appendTo('#element');
toast.show();

let listObjExpand: DropDownList = new DropDownList({
    index: 0,
    placeholder: 'Select a animate type',
    change: () => { valueChange();  }
});
listObjExpand.appendTo('#showAnimation');

let listObjCollapse: DropDownList = new DropDownList({
    placeholder: 'Select a animate type',
    change: () => { valueChange1();  }
});
listObjCollapse.appendTo('#hideAnimation');

document.getElementById('show_toast').onclick = () => {
    toast.show();
}

function valueChange(): void {
  toast.animation.show.effect = <Effect>(listObjExpand.value);
}

function valueChange1(): void {
  toast.animation.hide.effect = <Effect>(listObjCollapse.value);
}

```

{% endtab %}