---
title: "Set Essential JS 2 Tooltip to the commands"
component: "Toolbar"
description: "This example demonstrates how to set the Essential JS 2 Tooltip component to the Essential JS 2 Toolbar component commands."
---

# Set Essential JS 2 Tooltip to the commands

The [`tooltipText`](../../api/toolbar/item#tooltiptext) property of the Toolbar item is used to set the HTML Tooltip to the commands that can be viewed as hint texts on mouse hover.

To change the [`tooltipText`](../../api/toolbar/item#tooltiptext) to ej2-tooltip component:

* Import the `Tooltip` module from `ej2-popups`,and initialize the Tooltip with the Toolbar target. Refer to the following code example:

{% tab template="toolbar/toolbar-how-tooltip", es5Template="es5_toolbar_tooltip", sourceFiles="index.ts,index.html" %}

```typescript

import { Tooltip } from '@syncfusion/ej2-popups';
import { Toolbar } from '@syncfusion/ej2-navigations';

let toolbar: Toolbar = new Toolbar({
    width: 300,
    items: [
        { text: "Cut", tooltipText: 'Cut' },
        { text: "Copy", tooltipText: 'Copy' },
        { text: "Paste", tooltipText: 'Paste' },
        { text: "Undo", tooltipText: 'Undo' },
        { text: "Redo", tooltipText: 'Redo' }
    ]
});
toolbar.appendTo('#element');
let tooltip: Tooltip = new Tooltip({
  target: '#element [title]',
 });
tooltip.appendTo('#Tooltip');

```

{% endtab %}