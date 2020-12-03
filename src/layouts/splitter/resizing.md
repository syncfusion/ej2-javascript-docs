---
title: "Resize"
component: "Splitter"
description: "This section explain about split panes resizing behaviors."
---

# Resize

By default, resizing will be enable for split panes. Resizing gripper element will be add to the separator to makes the resize easy.

> Horizontal splitter will allows to resize in horizontal directions.
> Vertical splitter will allows to resize in vertical directions.

While resizing, previous and next panes will be adjust its dimensions automatically.

## Min and Max validation

Splitter allows you to set the [minimum](../api/splitter/paneProperties/#min) and [maximum](../api/splitter/paneProperties/#max) sizes for each pane. Resizing will not be occur over the minimum and maximum values.

{% tab template="splitter/resize-min-max" sourceFiles="app.ts,index.html,styles.css" es5Template="resizeminmax" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px', min: '20%', max: '40%'},
        { size: '200px', min: '30%', max: '60%'}
        { size: '200px'}
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## Prevent resizing

You can disable the resizing for the pane by setting `false` to the [`resizable`](../api/splitter/panePropertiesModel/#resizable) API within [paneSettings](../api/splitter/paneProperties/#paneproperties).

> Splitter resizing will be enabled only when the target of the adjacent pane's `resizable` api should also be in `true` state.

{% tab template="splitter/fixed-pane" sourceFiles="app.ts,index.html,styles.css" es5Template="disableresize" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px', min: '20%', max: '40%', resizable: false},
        { size: '200px', min: '30%', max: '60%'}
        { size: '200px'}
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## Refresh content on resizing

While resizing the panes, you can refresh the pane contents by using either [`resizeStart`](../api/splitter/#resizestart), [`resizing`](../api/splitter/#resizestart) or [`resizeStop`](../api/splitter/#resizestart) events.

## Customize the resize grip and cursor

You can customize the resize gripper icon and cursor in css level.

{% tab template="splitter/resizeicon" sourceFiles="app.ts,index.html,styles.css" es5Template="resizeicon" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px', min: '20%', max: '40%'},
        { size: '200px', min: '30%', max: '60%'}
        { size: '200px'}
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## See Also

* [Collapsible panes](./expand-and-collapse/)