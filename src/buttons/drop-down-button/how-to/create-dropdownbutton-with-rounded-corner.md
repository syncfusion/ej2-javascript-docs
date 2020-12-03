---
title: "Create DropDownButton with rounded corner"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Create DropDownButton with rounded corner

DropDownButton with rounded corner can be achieved by adding `border-radius` CSS property to button element.

In the following example, `e-round-corner` class is defined with `5px` `border-radius` property and added that class to button element using [`cssClass`](../../api/drop-down-button#cssclass) property.

{% tab template= "drop-down-button/rounded-drop-down", sourceFiles="app.ts,index.html,styles.css",
es5Template="rounded-template" %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
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
let drpDownBtn: DropDownButton = new DropDownButton({ items: items, cssClass: 'e-round-corner' });

// Render initialized DropDownButton.
drpDownBtn.appendTo('#element');
```

{% endtab %}