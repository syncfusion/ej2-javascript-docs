---
title: "Disable a DropDownButton"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Disable a DropDownButton

DropdownButton component can be enabled/disabled by giving [`disabled`](../../api/drop-down-button#disabled) property. It can be
disabled by setting disabled property as `true`.

{% tab template= "drop-down-button/disabled", sourceFiles="app.ts,index.html,styles.css",
es5Template="icons-template" %}

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
let drpDownBtn: DropDownButton = new DropDownButton({ iconCss: 'ddb-icons e-message', items: items, disabled: true }, '#iconbutton');
```

{% endtab %}