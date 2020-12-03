---
title: "SplitButton Icons and Separator"
component: "SplitButton"
description: "TypeScript SplitButton allows the end user to place the icons and separate popup items in DropDownButton."
---

# Icons and separator

## SplitButton icons

SplitButton can have an icon to provide the visual representation of the action. To place the icon on a SplitButton,
set the [`iconCss`](../api/split-button#iconcss) property to `e-icons` with the required icon CSS. By default, the icon is positioned
to the left side of the SplitButton. You can customize the icon's position by using the
[`iconPosition`](../api/split-button#iconposition) property.

In the following example, the SplitButton with default iconPosition and `iconPosition` as `Top` is showcased:

{% tab template= "split-button/icon", sourceFiles="app.ts,index.html,styles.css", es5Template="icons-template", isDefaultActive=true %}

```typescript
import { SplitButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let items: ItemModel[] = [
    {
        text: 'Undo'
    },
    {
        text: 'Redo'
    },
    {
        text: 'Cut'
    },
    {
        text: 'Copy'
    },
    {
        text: 'Paste'
    }];

//To place the icon in SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb-icons e-paste', items: items }, '#iconbutton');
let splitBtnObj: SplitButton = new SplitButton({ iconCss: 'e-sb-icons e-paste', items: items, iconPosition: "Top" }, '#iconpstn');
```

{% endtab %}

> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element.
You can also use third party icons on the splitBtn using the [`iconCss`](../api/split-button#iconcss)property.

### Vertical button

Vertical Button in SplitButton can be achieved by adding `e-vertical` class using [`cssClass`](../api/split-button#cssclass) property.

The following example illustrates how to provide vertical support in SplitButton component.

{% tab template= "split-button/vertical", sourceFiles="app.ts,index.html,styles.css", es5Template="vertical-template" %}

```typescript
import { SplitButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let items: ItemModel[] = [
    {
        text: 'Undo'
    },
    {
        text: 'Redo'
    },
    {
        text: 'Cut'
    },
    {
        text: 'Copy'
    },
    {
        text: 'Paste'
    }];

//To position the icon to the top of the text on a SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb-icons e-paste', cssClass: 'e-vertical', items: items, iconPosition: 'Top' }, '#iconbutton');
```

{% endtab %}

> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element.
You can also use third party icons on the SplitButton using the [`iconCss`](../api/split-button#iconcss) property.

## Separator

The Separators are the horizontal lines that are used to separate the popup items. You `cannot` select the separators.
You can enable separators to group the popup items using the `separator` property.

The following example illustrates how to enable separator support in SplitButton component.

{% tab template= "split-button/seperator", sourceFiles="app.ts,index.html,styles.css",
es5Template="seperator-template" %}

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
    },
    {
        separator: true
    },
    {
        text: 'Font',
        iconCss: 'e-sb-icons e-font'
    },
    {
        text: 'Paragraph',
        iconCss: 'e-sb-icons e-paragraph'
    }];

//To position the separator in SplitButton.
let splitBtn: SplitButton = new SplitButton({ iconCss: 'e-sb-icons e-paste', items: items }, '#iconbutton');
```

{% endtab %}

## See Also

* [SplitButton popup with icons](./popup-items#icons)
