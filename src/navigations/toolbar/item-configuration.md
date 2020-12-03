---
title: "Toolbar Item configuration"
component: "Toolbar"
description: "Toolbar items are constructed with built-in command types or item templates such as separator, button, and input."
---

# Item Configuration

The Toolbar can be rendered by defining an array of [`items`](../api/toolbar#items).  Items can be constructed with the following built-in command types or item template.

## Button

`Button` is the default command [`type`](../api/toolbar/item#type), and it can be rendered by using the [`text`](../api/toolbar/item#text) property.
Properties of the button command type:

  Property   | Description
------------ | -------------
  [`text`](../api/toolbar/item#text)  | The text to be displayed for button.
 [`id`](../api/toolbar/item#id)  | The ID of the button to be rendered. If the ID is not given, auto ID is generated.
  [`prefixIcon`](../api/toolbar/item#prefixicon) | Defines the class used to specify an icon for the button. The icon is `positioned before` the text if text is available or the icon alone button is rendered.
[`suffixIcon`](../api/toolbar/item#suffixicon) | Defines the class used to specify an icon for the button. The icon is `positioned after` the text if text is available. If both [`prefixIcon`](../api/toolbar/item#prefixicon) and [`suffixIcon`](../api/toolbar/item#suffixicon) are specified, only `prefixIcon` is considered.
  [`width`](../api/toolbar/item#width)   | Used to set the [`width`](../api/toolbar/item#width) of the button.
  [`align`](../api/toolbar/item#align)  | Specifies the location for aligning Toolbar items.

## Separator

The `Separator` type adds a vertical separation between the Toolbar's single/multiple commands.

{% tab template="toolbar/toolbar-items", es5Template="es5_toolbar_items", sourceFiles="index.ts,index.html" %}

```typescript

import {Toolbar} from '@syncfusion/ej2-navigations';
let toolbar: Toolbar = new Toolbar({
    items: [
        { text: "Cut" },
        { text: "Copy" },
        { type: "Separator" },
        { text: "Paste" },
        { type: "Separator" },
        { text: "Undo" },
        { text: "Redo" }
    ]
});
toolbar.appendTo('#element');

```

{% endtab %}

> If `Separator` is added as the first or the last item, it will not be visible.

## Input

The `Input` type is only applicable for adding `template` elements when the [`template`](../api/toolbar/item#template) property is defined as an `object`.  Input type creates an `input element` internally that acts as the container for `Syncfusion` input based components.

### NumericTextBox

* The `NumericTextBox` component can be included by importing the `NumericTextBox` module from `ej2-inputs`.

* Initialize the `NumericTextBox` in template property, where the Toolbar item type is set as `Input`.

* Related `NumericTextBox` component properties can also be configured as given below.

```javascript
new NumericTextBox( { format: 'c2' }))
```

### DropDownList

* The `DropDownList` component can be included by importing the `DropDownList` module from `ej2-dropdowns`.

* Initialize the `DropDownList` in template property, where the Toolbar item type is set as `Input`.

* Related `DropDownList` component properties can also be configured as given below.

```javascript
new DropDownList({ width:100 })
```

### CheckBox

* The `CheckBox` component can be included by importing the `CheckBox` module from `ej2-buttons`.

* Initialize the `CheckBox` in template property, where the Toolbar item type is set as `Input`.

* Related `CheckBox` component properties can also be configured as given below.

```javascript
new CheckBox({ label: 'Default' })
```

### RadioButton

* The `RadioButton` component can be included by importing the `RadioButton` module from `ej2-buttons`.

* Initialize the `RadioButton` in template property, where the Toolbar item type is set as `Input`.

* Related `RadioButton` component properties can also be configured as given below.

```javascript
new RadioButton({ label: 'Option 1', name: 'default'})
```

The above steps are applicable for all 'Syncfusion' input based components.

E.g.: The following code explains how to add `NumericTextBox`,`DropDownList`,`RadioButton` and `CheckBox` components to the Toolbar.

{% tab template="toolbar/toolbar-items", es5Template="es5_toolbar_items_input", sourceFiles="index.ts,index.html" %}

```typescript

import { Toolbar } from '@syncfusion/ej2-navigations';
import { NumericTextBox} from '@syncfusion/ej2-inputs';
import { DropDownList} from '@syncfusion/ej2-dropdowns';
import { CheckBox, RadioButton  } from '@syncfusion/ej2-buttons';

let sportsData: string[] = ['Badminton', 'Cricket', 'Football', 'Golf', 'Tennis'];
let toolbar: Toolbar = new Toolbar({
    items: [
        { text: "Cut" },
        { text: "Copy" },
        { type: "Separator" },
        { text: "Undo" },
        { text: "Redo" },
        { type: "Separator" },
        { type: 'Input', template: new NumericTextBox({ format: 'c2', value:1, width:150 }) },
        { type: "Separator" },
        { type: 'Input', template: new DropDownList({ dataSource: sportsData, width: 120, index: 2 }) },
        { type: "Separator" },
        { type: 'Input', template: new CheckBox({ label: 'Checkbox', checked: true }) },
        { type: "Separator" },
        { type: 'Input', template: new RadioButton({ label: 'Radio', name: 'default', checked: true }) }
    ]
});
toolbar.appendTo('#element');
```

{% endtab %}

## See Also

* [How to set item wise custom template](./how-to/set-item-wise-custom-template)