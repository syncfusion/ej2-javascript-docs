---
title: "Pane Content"
component: "Splitter"
description: "This section explains about user can feed pane sizes."
---

# Pane Sizing

Splitter allows you to provide pane sizes either in `pixel` or `percentage` formats.

## Auto size panes

The splitter's panes are adjusted automatically during resizing if the size is not specified externally to panes, because the panes are designed based on flex layout by default. When add/remove or show/hide the panes, the panes are auto aligned within its container.

{% tab template="splitter/layouts" sourceFiles="app.ts,index.html,styles.css" es5Template="layouts-sizes" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## Fixed pane

You can render the split panes with fixed size in both `horizontal` and `vertical` mode. Even if you provide fixed sizes to all the panes, the last pane is considered as a flexible pane.

{% tab template="splitter/pansizing" sourceFiles="app.ts,index.html,styles.css" es5Template="pansizing" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px' },
        { size: '200px' },
        { size: '200px' }
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

{% tab template="splitter/pansizing" sourceFiles="app.ts,index.html,styles.css" es5Template="pansizing-percentage" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '30%' },
        { size: '40%' },
        { size: '30%' }
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}