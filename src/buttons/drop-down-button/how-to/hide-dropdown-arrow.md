---
title: "Hide dropdown arrow"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Hide dropdown arrow

You can hide the dropdown arrow from the DropDownButton by adding class `e-caret-hide` to DropDownButton element using
[`cssClass`](../../api/drop-down-button#cssclass) property.

{% tab template= "drop-down-button/hide", sourceFiles="app.ts,index.html,styles.css",
es5Template="hide-arrow-template", isDefaultActive=true %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

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

// To initialize the DropDownButton component without down arrow.
let drpDownBtn: DropDownButton = new DropDownButton({ items: items, cssClass: 'e-caret-hide' });
// Render initialized DropDownButton.
drpDownBtn.appendTo('#hide');

```

{% endtab %}