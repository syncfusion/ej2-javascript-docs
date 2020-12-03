---
title: "SplitButton Popup Items"
component: "SplitButton"
description: "TypeScript SplitButton allows the end user to customize the whole popup or action items in popup using templates, and to place icons in popup items."
---

# Popup Items

## Icons

The Popup action item have an icon or image to provide visual representation of the action. To place the icon on a popup item,
set the [`iconCss`](../api/split-button#iconcss) property to `e-icons` with the required icon CSS. By default, the icon is
positioned to the left side of the popup action item.

In the following sample, the icons for Cut, Copy, and Paste menu items are
added using the iconCss property.

{% tab template= "split-button/popup-icon", sourceFiles="app.ts,index.html,styles.css", es5Template="icons-template", isDefaultActive=true %}

```typescript
import { SplitButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let items: ItemModel[] = [
    {
        text: 'Cut',
        iconCss: 'e-sb-icons e-cut'
    },
    {
        text: 'Copy',
        iconCss: 'e-icons e-copy'
    },
    {
        text: 'Paste',
        iconCss: 'e-sb-icons e-paste'
    }];

//To position the icons in SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb-icons e-paste', items: items }, '#iconbutton');

```

{% endtab %}

## Template

### Item templating

Popup items can be customized by using the [`beforeItemRender`](../api/split-button#beforeitemrender) event. The item render event
triggers while rendering each Popup action item. The event argument will be used to identify the action item and customize it
based on the requirement.

In the following example, the icons in each [`li`] items is right aligned by appending span element while [`li`] rendering:

{% tab template= "split-button/template", sourceFiles="app.ts,index.html,styles.css", es5Template="item-template" %}

```typescript
import { SplitButton, ItemModel, SplitButtonModel,MenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { enableRipple, createElement } from '@syncfusion/ej2-base';

enableRipple(true);

let items: ItemModel[] =  [
    {
       text: 'Cut',
     },
     {
       text: 'Copy',
     },
     {
       text: 'Paste',
      }
   ];

let menuOptions: SplitButtonModel = {
        items: items,
        iconCss: 'e-sb-icons e-paste',
        beforeItemRender: (args: MenuEventArgs) => {
          let shortCutSpan: HTMLElement = createElement('span');
            let text: string = args.item.text;
            args.element.appendChild(shortCutSpan);
            shortCutSpan.setAttribute('class','shortcut');
            let clsName: string = (text === 'Copy') ? 'e-icons' : 'e-sb-icons';
            shortCutSpan.classList.add(clsName);
            (text === 'Cut') ? shortCutSpan.classList.add('e-cut') : (text === 'Paste') ? shortCutSpan.classList.add('e-paste') : shortCutSpan.classList.add('e-copy');
        }
    };

let splitBtn: SplitButton = new SplitButton(menuOptions, '#action');

```

{% endtab %}

### Popup templating

The whole popup can be customized as per the requirement and it can be customized by handling it in
[`target`](../api/split-button#target) property.

In the following sample, the whole popup item is customized as color palette by giving `div` as target and it can be achieved
using `target` property.

{% tab template= "split-button/popup-template", sourceFiles="app.ts,index.html,styles.css", es5Template="item-template" %}

```typescript
import { SplitButton, SplitButtonModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let menuOptions: SplitButtonModel = {
        target: '#dropdowntarget',
        iconCss: 'e-sb-icons e-color',
    };

let splitBtn: SplitButton = new SplitButton(menuOptions, '#action');

```

{% endtab %}

## See Also

* [Popup items grouping](./how-to/group-items-in-popup)
* [SplitButton popup with separator](./icons-and-separator#separator)