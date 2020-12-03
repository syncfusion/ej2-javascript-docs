---
title: "Set the disabled state"
component: "SplitButton"
description: "TypeScript SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Set the disabled state

SplitButton component can be enabled or disabled using [`disabled`](../../api/split-button#disabled) property. To disable SplitButton component, set the disabled
property as `true`.

The following example illustrates how to set the disable state in SplitButton component.

{% tab template= "split-button/disabled", sourceFiles="app.ts,index.html,styles.css",
es5Template="disabled-template", isDefaultActive=true %}

```typescript
import { SplitButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let items: ItemModel[] = [
    {
        text: 'Autosum'
    },
    {
        text: 'Average'
    },
    {
        text: 'Count numbers',
    },
    {
        text: 'Min'
    },
    {
        text: 'Max'
    }];

//To disable the SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb e-sigma', items: items, disabled: true }, '#iconbutton');
```

{% endtab %}