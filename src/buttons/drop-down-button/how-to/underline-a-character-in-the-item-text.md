---
title: "Underline a character in the item text"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Underline a character in the item text

Underline a particular character in a text can be handled in
[`beforeItemRender`](../../api/drop-down-button#beforeitemrender)event by adding `<u>` tag in between the text and given
as innerHTML in `li` rendering.

In the following example, `C` is underlined in the text `Copy`.

{% tab template= "drop-down-button/underline", sourceFiles="app.ts,index.html,styles.css",
es5Template="underline-template" %}

```typescript
import { DropDownButton, DropDownButtonModel, ItemModel, MenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Cut'
    },
    {
        text: 'Copy'
    },
    {
        text: 'Paste'
    }];

// Initialize DropDownButton options.
let ddbOption: DropDownButtonModel = {
  items: items,
  beforeItemRender: (args: MenuEventArgs) => {
    if (args.item.text === 'Copy') {
        //To underline a particular text.
        args.element.innerHTML = '<u>C</u>opy';
    }
}
}
// Initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton(ddbOption);

// Render initialized DropDownButton.
drpDownBtn.appendTo('#element');

```

{% endtab %}