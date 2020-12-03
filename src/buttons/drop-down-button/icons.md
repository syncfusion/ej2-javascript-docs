---
title: "DropDownButton Icons"
component: "DropDownButton"
description: "TypeScript DropDownButton allows the end user to place the icons/sprite images in DropDownButton."
---

# Icons

## DropDownButton icons

DropdownButton can have an icon to provide the visual representation of the action. To place the icon on a DropdownButton,
set the [`iconCss`](../api/drop-down-button#iconcss) property to `e-icons` with the required icon CSS. By default,
the icon is positioned to the left side of the DropdownButton. You can customize the icon's position using
the [`iconPosition`](../api/drop-down-button#iconcss) property.

In the following example, the DropdownButton with default iconPosition and iconPosition as `Top` is showcased:

{% tab template= "drop-down-button/icon", sourceFiles="app.ts,index.html,styles.css", es5Template="icons-template", isDefaultActive=true %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Edit'
    },
    {
        text: 'Delete'
    },
    {
        text: 'Mark as Read'
    },
    {
        text: 'Like Message'
    }];
// To initialize the DropDownButton with icon.
let drpDownBtn: DropDownButton = new DropDownButton({ iconCss: 'ddb-icons e-message', items: items }, '#iconbutton');
// To position the icon to the top of the text on a DropDownButton.
let dropDownBtnObj: DropDownButton = new DropDownButton({ iconCss: 'ddb-icons e-message', items: items, iconPosition: 'Top' }, '#iconpstn');
```

{% endtab %}

### Icon only DropDownButton

Icon only DropDownButton can be achieved by using [`iconCss`](../api/drop-down-button#iconcss) property and to hide drop down arrow
`e-caret-hide` class is added using [`cssClass`](../api/drop-down-button#cssclass) property.

{% tab template= "drop-down-button/icon-only", sourceFiles="app.ts,index.html,styles.css", es5Template="icon-only-template" %}

```typescript
import { DropDownButton, ItemModel, DropDownButtonModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'New tab'
    },
    {
        text: 'New window'
    },
    {
        text: 'New incognito window'
    },
    {
        separator: true
    },
    {
        text: 'Print'
    },
    {
        text: 'Cast'
    },
    {
        text: 'Find'
    }];

// Initialize DropDownButton options.
let options: DropDownButtonModel = {
  items: items,
  iconCss: 'e-icons e-menu',
  cssClass: 'e-caret-hide'
};

// To initialize the icon only DropDownButton.
let drpDownBtn: DropDownButton = new DropDownButton(options);
drpDownBtn.appendTo('#icononly');
```

{% endtab %}

> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element.
You can also use third party icons on the DropDownButton using the [`iconCss`](../api/drop-down-button#iconcss) property.

### DropDownButton with sprite image

Sprite images can be loaded in DropDownButton instead of font icons using [`iconCss`](../api/drop-down-button#iconcss) property.

In this following example, `e-image` class is added with background url of the sprite image along with X and Y positions. The `width` and
`height` of the element set as `32px`.

{% tab template= "drop-down-button/sprite", sourceFiles="app.ts,index.html,styles.css", es5Template="sprite-template" %}

```typescript
import { DropDownButton, ItemModel, DropDownButtonModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Display Settings'
    },
    {
        text: 'System Settings'
    },
    {
        text: 'Additional Settings'
    }];

// Initialize DropDownButton options.
let options: DropDownButtonModel = {
  items: items,
  cssClass: 'e-caret-hide',
  iconCss: 'e-image'
};

// To initialize the DropDownButton with sprite image.
let drpDownBtn: DropDownButton = new DropDownButton(options);
drpDownBtn.appendTo('#icononly');
```

{% endtab %}

## Vertical button

Vertical button in DropDownButton can be achieved by adding `e-vertical` class using [`cssClass`](../api/drop-down-button#cssclass) property.

The following example illustrates how to provide vertical support in DropDownButton component.

{% tab template= "drop-down-button/vertical", sourceFiles="app.ts,index.html,styles.css", es5Template="vertical-template" %}

```typescript
import { DropDownButton, ItemModel } from '@syncfusion/ej2-splitbuttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Edit'
    },
    {
        text: 'Delete'
    },
    {
        text: 'Mark as Read'
    },
    {
        text: 'Like Message'
    }];

// To initialize the vertical DropDownButton.
let drpDownBtn: DropDownButton = new DropDownButton({ iconCss: 'ddb-icons e-message', cssClass: 'e-vertical', items: items, iconPosition: 'Top' }, '#iconbutton');
```

{% endtab %}

## See Also

* [Dropdown popup with icons](./popup-items#icons)
* [Customized icon size](./how-to/customize-icon-and-width)