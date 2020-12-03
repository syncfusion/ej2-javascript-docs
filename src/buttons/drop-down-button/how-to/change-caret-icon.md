---
title: "Change caret icon"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Change caret icon

Dropdown arrow can be customized on popup open and close. It can be handled in [`beforeOpen`](../../api/drop-down-button#beforeopen)
and [`beforeClose`](../../api/drop-down-button#beforeclose) event.

In the following example, the up arrow is updated on popup close and down arrow is updated on popup open using `beforeOpen`
and `beforeClose` event by adding and removing `e-caret-up` class.

{% tab template= "drop-down-button/up-down-arrow", sourceFiles="app.ts,index.html,styles.css",
es5Template="up-down-template" %}

```typescript
import { DropDownButton, ItemModel, BeforeOpenCloseMenuEventArgs, DropDownButtonModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple, createElement } from '@syncfusion/ej2-base';

enableRipple(true);
// Initialize action items.
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

// Initialize DropDownButton options.
let options: DropDownButtonModel = {
  items: items,
 // Removing 'e-caret-up' class.
  beforeClose: (args: BeforeOpenCloseMenuEventArgs) => {
     drpDownBtn.cssClass = '';
  },
  // Adding 'e-caret-up' class.
  beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
     drpDownBtn.cssClass = 'e-caret-up';
  }
};
// To initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton(options);
// Render initialized DropDownButton.
drpDownBtn.appendTo('#arrow');
```

{% endtab %}