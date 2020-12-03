---
title: "Create right-to-left SplitButton"
component: "SplitButton"
description: "TypeScript SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Create right-to-left SplitButton

SplitButton component has RTL support. This can be achieved by setting [`enableRtl`](../../api/split-button#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in SplitButton component.

{% tab template= "split-button/disabled", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template" %}

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

//To enable RTL in SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb e-sigma', items: items, enableRtl: true }, '#iconbutton');
```

{% endtab %}
