---
title: "Position popup open"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Position popup open

Popup open position can be changed according to the requirement. Popup open position can be changed in
[`open`](../../api/drop-down-button#open) event by setting `top` and `left` for the popup element.

In the following example, the `top` position of the popup element is changed in `open` event.

{% tab template= "drop-down-button/position", sourceFiles="app.ts,index.html,styles.css",
es5Template="position-template" %}

```typescript
import { DropDownButton, ItemModel, OpenCloseMenuEventArgs, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Cut'
    },
    {
        text: 'Copy'
    },
    {
        text: 'Paste'
    }];

// Initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton({
  items: items,
  cssClass: 'e-caret-up',
  // To position dropDownButton popup.
  open: (args: OpenCloseMenuEventArgs) => {
    args.element.parentElement.style.top = drpDownBtn.element.getBoundingClientRect().top - args.element.parentElement.offsetHeight +'px';
  }
});

// Render initialized DropDownButton.
drpDownBtn.appendTo('#element');
```

{% endtab %}