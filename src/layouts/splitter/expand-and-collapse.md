---
title: "Expand and Collapse"
component: "Splitter"
description: "This section explains about how to configure collapsible splitter panes, which helps to do expand and collapse action dynamically."
---

# Expand and Collapse

## Collapsible panes

The Splitter panes can be configured with built-in expand and collapse functionalities. By default, the collapsible behavior is disabled. Enable the [collapsible](../api/splitter/paneProperties/#collapsible) behavior in the paneSettings property to show or hide the expand or collapse icons in the panes. You can dynamically expand and collapse the panes by the corresponding icons.

The following code shows how to enable collapsible behavior.

{% tab template="splitter/expand-collapse", isDefaultActive = "false", sourceFiles="app.ts,index.html,index.css" es5Template="expand-collapse-es5" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '250px',
    paneSettings: [
        { collapsible: true },
        { collapsible: true },
        { collapsible: true }
    ],
    separatorSize: 2,
    width: '100%'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## Programmatically control the expand and collapse action

The Splitter provides public method to control the expand and collapse behavior programmatically using the [expand](../api/splitter/#expand) and [collapse](../api/splitter/#collapse) methods. Refer to the following code example.

{% tab template="splitter/expand-collapse-method", isDefaultActive = "false", sourceFiles="app.ts,index.html,index.css" es5Template="expand-collapse-method-es5" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '230px',
    paneSettings: [
        { collapsible: true },
        { collapsible: true },
        { collapsible: true }
    ],
    width: '100%'
});
splitObj.appendTo('#splitter');

document.getElementById('expand').onclick = (): void => {
   splitObj.expand(0);
}
document.getElementById('collapse').onclick = (): void => {
   splitObj.collapse(0);
}

```

{% endtab %}

## Specify initial state to panes

You can render specific panes with collapsed state on page load. Specify a Boolean value to the [collapsed](../api/splitter/#collapsed) property to control this behavior. The following code explains how to collapse panes on rendering (the second panes renders with collapsed state).

{% tab template="splitter/collapsed", isDefaultActive = "false", sourceFiles="app.ts,index.html,index.css" es5Template="collapsed-es5" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '250px',
    paneSettings: [
        { collapsible: true },
        { collapsible: true, collapsed: true },
        { collapsible: true }
    ],
    width: '100%'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)