---
title: "Create right-to-left DropDownButton"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Create right-to-left DropDownButton

DropDownButton component has RTL support. This can be achieved by setting [`enableRtl`](../../api/drop-down-button#enablertl) as true.

The following example illustrates how to enable right-to-left support in DropDownButton component.

{% tab template= "drop-down-button/disabled", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template" %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Edit'
    },
    {
        text: 'Delete'
    },
    {
        text: 'Mark as Read'
    },
    {
        text: 'Like Message'
    }];

//To initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton({ iconCss: 'ddb-icons e-message', items: items, enableRtl: true }, '#iconbutton');
```

{% endtab %}