---
title: "Underline a character in a text"
component: "SplitButton"
description: "TypeScript SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Underline a character in a text

Underline a particular character in a text can be handled in [`beforeItemRender`](../../api/split-button#beforeitemrender) event
by adding `<u>` tag in between the text and given as innerHTML in `li` rendering.

In the following example, `C` is underlined in the text `Copy`.

{% tab template= "split-button/underline", sourceFiles="app.ts,index.html,styles.css",
es5Template="underline-template" %}

```typescript
import { SplitButton, ItemModel, MenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Initialize action items.
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

let splitBtn: SplitButton = new SplitButton({
    content: 'Paste',
    items: items,
    beforeItemRender: (args: MenuEventArgs) => {
        if (args.item.text === 'Copy') {
            args.element.innerHTML = '<u>C</u>opy';
        }
    }
}, '#element');

```

{% endtab %}