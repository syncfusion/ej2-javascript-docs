---
title: "Customize icon and width"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Customize icon and width

Width of the DropDownButton can be customized by setting required width to the dropdown element.

The following UI can be achieved by setting [`iconPosition`](https://ej2.syncfusion.com/documentation/api/drop-down-button/dropDownButtonModel/#iconposition) as `Top`, width as `85px` and size of the
font icon as `40px` by adding `e-custom` class.

{% tab template= "drop-down-button/custom-width", sourceFiles="app.ts,index.html,styles.css",
es5Template="custom-width-template" %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Find'
    },
    {
        text: 'Replace'
    },
    {
        text: 'Go To'
    },
    {
        text: 'Go To Special'
    }];

// To initialize DropDownButton with `e-custom` class.
let drpDownBtn: DropDownButton = new DropDownButton({
    iconCss: 'e-icons e-search',
    cssClass: 'e-custom',
    items: items,
    iconPosition: 'Top'
    }, '#iconbutton'
);
```

{% endtab %}