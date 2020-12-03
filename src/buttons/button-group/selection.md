---
title: "ButtonGroup Selection and Nesting"
component: "ButtonGroup"
description: "ButtonGroup supports single selection, multiple selection, nesting with dropdownbutton and splitbutton components."
---

# Selection and Nesting

## Selection

### Single selection

ButtonGroup supports radio type selection in which only one button can be selected. This can be achieved by adding input element
along with `id` attribute with its corresponding label along with `for` attribute inside the target element. In this ButtonGroup,
the type of the input element should be `radio` and `e-btn` is added to the `label` element.

The following example illustrates the single selection behavior in ButtonGroup.

{% tab template= "button-group/radio", sourceFiles="index.html,styles.css", isDefaultActive=true %}

{% endtab %}

### Multiple selection

ButtonGroup supports checkbox type selection in which multiple button can be selected. This can be achieved by adding input element
along with `id` attribute with its corresponding label along with `for` attribute inside the target element. In this ButtonGroup,
the type of the input element should be `checkbox` and `e-btn` is added to the `label` element.

The following example illustrates the multiple selection behavior in ButtonGroup.

{% tab template= "button-group/checkbox", sourceFiles="index.html,styles.css" %}

{% endtab %}

## Nesting

Nesting with other components can be possible in ButtonGroup. The following components can be nested in ButtonGroup.
* DropDownButton
* SplitButton

For nesting support, [`SplitButton dependencies`](./../split-button/getting-started#dependencies) should be configured and added in `system.config.js`.

### DropDownButton

To initialize DropDownButton component, refer [`DropDownButton Getting Started documentation`](./../drop-down-button/getting-started).

In the following example, the DropDownButton component can be added by creating button element with ID as `dropdownelement` in `index.html`and
import the DropDownButton in `script` file, and initialize with the `dropdownelement`.

{% tab template= "button-group/drop-down-button", sourceFiles="app.ts,index.html,styles.css", es5Template="drop-down-template" %}

```typescript

import { DropDownButton, ItemModel, DropDownButtonModel } from '@syncfusion/ej2-splitbuttons';

let items: ItemModel[] = [
{
    text: 'Learn SQL'
},
{
    text: 'Learn PHP'
},
{
    text: 'Learn Bootstrap'
}];

let menuOptions: DropDownButtonModel = {
    items: items
};

// To render DropDownButton.
let btnObj: DropDownButton = new DropDownButton(menuOptions);
btnObj.appendTo('#dropdownelement');

```

{% endtab %}

### SplitButton

To initialize SplitButton component, refer [`SplitButton Getting Started documentation`](./../split-button/getting-started).

In the following example, the SplitButton component can be added by creating button element with ID as `splitbuttonelement` in `index.html`and
import the SplitButton in `app.ts` file, and initialize with the `splitbuttonelement`.

{% tab template= "button-group/split-button", sourceFiles="app.ts,index.html,styles.css", es5Template="split-button-template" %}

```typescript

import { SplitButton, ItemModel } from '@syncfusion/ej2-splitbuttons';

let items: ItemModel[] = [
{
    text: 'Paste'
},
{
    text: 'Paste Text'
},
{
    text: 'Paste Special'
}];

// To render SplitButton.
let btnObj: SplitButton = new SplitButton({items: items});
btnObj.appendTo('#splitbuttonelement');

```

{% endtab %}

## See Also

* [Show ButtonGroup selected state on initial render](./how-to/show-buttongroup-selected-state-on-initial-render)