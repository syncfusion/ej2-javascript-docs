---
title: "Split Panes"
component: "Splitter"
description: "This section explain about split panes behaviours."
---

# Split Panes

This section explain about split panes behaviours.

## Horizontal layout

By default, splitter will render in horizontal orientation. Splitter container will be splitted as panes in horizontal flow direction with vertical seperator.

{% tab template="splitter/layouts" sourceFiles="app.ts,index.html,index.css" es5Template="layouts-horizontal" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

// Initialize Splitter control
let splitObject: Splitter = new Splitter({
    height: '250px',
    paneSettings: [
        { size: '200px' },
        { size: '200px' },
        { size: '200px' }
    ],
    width: '600px'
});

// Render initialized Splitter
splitObject.appendTo('#splitter');
```

{% endtab %}

## Vertical layout

By setting [orientation](../api/splitter/#orientation) API as `Vertical`, splitter will render in vertical orientation. Splitter container will be splitted as panes in vertical flow direction with horizontal seperator.

{% tab template="splitter/layouts-orientation" sourceFiles="app.ts,index.html,index.css" es5Template="layouts-vertical" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

// Initialize Splitter control
let splitObject: Splitter = new Splitter({
    height: '305px',
    paneSettings: [
        { size: '100px' },
        { size: '100px' },
        { size: '100px' }
    ],
    width: '600px',
    orientation: 'Vertical'

});

// Render initialized Splitter
splitObject.appendTo('#splitter');
```

{% endtab %}

> You can also render multiple panes in splitter with both `Horizontal/Vertical` orientations.

## Separator

By default, pane separator will be render with `1px` width/height. You can customize the separator size by using [separatorSize](../api/splitter/#separatorsize) API.

> For horizontal orientation, it will be considered as separator width.
> For vertical orientation, it will be considered as separator height.

{% tab template="splitter/layouts" sourceFiles="app.ts,index.html,index.css" es5Template="layouts-separator" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

// Initialize Splitter control
let splitObject: Splitter = new Splitter({
    height: '250px',
    paneSettings: [
        { size: '200px' },
        { size: '200px' },
        { size: '200px' }
    ],
    width: '600px',
    separatorSize: '5'

});

// Render initialized Splitter
splitObject.appendTo('#splitter');
```

{% endtab %}

## Nested Splitter

Splitter provides support to render the nested pane to achieve the complex layouts. You can use the same `<div>` element for splitter pane and nested splitter.

> Also you can render the nested splitter using direct child of the splitter pane. For this, nested splitter should have `100%` width and height to match with the parent pane dimensions.

{% tab template="splitter/layouts-nested" sourceFiles="app.ts,index.html,index.css" es5Template="layouts-nested" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let horizontalObj: Splitter = new Splitter({
    height: '316px',
    paneSettings: [
        { size: '200px' },
        { size: '200px' },
        { size: '200px' }
    ],
    width: '600px'
});
horizontalObj.appendTo('#Horizontal_splitter');

let verticalObj: Splitter = new Splitter({
    height: '308px',
    paneSettings: [
        { size: '150px', min: '20%' },
        { size: '100px', min: '20%' }
    ],
    orientation: 'Vertical'
});
verticalObj.appendTo('#vertical_splitter');
```

{% endtab %}

## Add or remove pane

You can add the panes programmatic but it will makes you complex. For this, you can use the addPane/removePane methods to add and remove the panes dynamically in the splitter.

### Add pane

You can add the panes dynamically in the splitter by passing [paneProperties](../api/splitter/panePropertiesModel) along with index to the [addPane](../api/splitter/#addpane) method

{% tab template="splitter/addpane" sourceFiles="app.ts,index.html,index.css" es5Template="addpane" %}

```typescript
import { Splitter, PanePropertiesModel } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '190px'},
        { size: '190px'}
    ],
    width: '600px',
    created: onSplitterCreate
});
splitObj.appendTo('#splitter');


let paneDetails : PanePropertiesModel = {
    size: '190px',
    content: 'New Pane',
    min: '30px',
    max: '250px',
}

function onSplitterCreate() {
    document.getElementById('addpane').addEventListener('click', () => {
        splitObj.addPane(paneDetails, 1);
    })
}
```

{% endtab %}

### Remove pane

You can remove the split panes dynamically by passing the pane index to [removePane](../api/splitter/#removepane) method.

{% tab template="splitter/removepane" sourceFiles="app.ts,index.html,index.css" es5Template="removepane" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px'},
        { size: '200px'},
        { size: '200px'}
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

document.getElementById('removepane').addEventListener('click', () => {
    if (!isNullOrUndefined(document.querySelector('#splitter').querySelectorAll('.e-pane-horizontal')[1]))
    {
        splitObj.removePane(1);
    }
})
```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)
* [Collapsible panes](./expand-and-collapse/)
* [Define size to a panes](./pane-sizing/)
* [Specify content to a panes](./pane-content/)