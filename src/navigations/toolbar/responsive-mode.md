---
title: "Toolbar Responsive"
component: "Toolbar"
description: "Toolbar has responsive support to adapt toolbar component’s width based on the devices like mobile and tablet."
---

# Responsive Mode

This section explains the supported display modes of the Toolbar when the content exceeds the viewing area. Possible modes are:

* Scrollable
* Popup

## Scrollable

The default overflow mode of the Toolbar is `Scrollable`. Scrollable display mode supports display of commands in a single line with horizontal scrolling enabled when commands overflow to available space.

* The right and left navigation arrows are added to the start and end of the Toolbar to navigate to hidden commands.
* You can also see the hidden commands using touch swipe action.
* By default, if navigation icon in the `left` side is disabled, you can see the hidden commands by moving to the `right`.
* By clicking the arrow or by holding the arrow continuously,  hidden commands will become visible.
* If device navigation icons are not available, you can touch swipe to see the hidden commands of the Toolbar.

![Scrollable](./images/scrolling.gif)

* Once the Toolbar reaches the last or first command, the  corresponding navigation icon will be disabled and you can move to the opposite direction.

![Touch scroll](./images/scrolling_touch.gif)

![Swipe scroll](./images/scrolling_swipe.gif)

* You can continuously scroll the Toolbar content by holding the navigation icon.

![Long press scroll](./images/scrolling_long_press.gif)

{% tab template="toolbar/toolbar-scrollable", es5Template="es5_toolbar_scrollable", sourceFiles="index.ts,index.html,index.css" %}

```typescript

import {Toolbar} from '@syncfusion/ej2-navigations';

let toolbar: Toolbar = new Toolbar({
    width:600,
    items: [
            { type: 'Button', prefixIcon: 'e-cut-icon tb-icons', text:'Cut' },
            { type: 'Button', prefixIcon: 'e-copy-icon tb-icons', text:'Copy' },
            { type: 'Button', prefixIcon: 'e-paste-icon tb-icons', text:'Paste' },
            { type: 'Separator'},
            { type: 'Button', prefixIcon: 'e-bold-icon tb-icons', text:'Bold' },
            { type: 'Button', prefixIcon: 'e-underline-icon tb-icons', text:'Underline' },
            { type: 'Button', prefixIcon: 'e-italic-icon tb-icons', text:'Italic' },
            { type: 'Button', prefixIcon: 'e-color-icon tb-icons', text:'Color-Picker' },
            { type: 'Separator'},
            { type: 'Button', prefixIcon: 'e-ascending-icon tb-icons', text:'A-Z Sort' },
            { type: 'Button', prefixIcon: 'e-descending-icon tb-icons', text:'Z-A Sort' },
            { type: 'Button', prefixIcon: 'e-clear-icon tb-icons', text:'Clear' }
          ]
});
toolbar.appendTo('#element');

```

{% endtab %}

## Popup

`Popup` is another type of [`overflowMode`](../api/toolbar#overflowmode) in which the Toolbar container holds the commands that can be placed in the available space. The rest of the overflowing commands that do not fit within
the viewing area moves to the overflow popup container.

The commands placed in the popup can be viewed by opening the popup using the drop down icon given at the end of the Toolbar.

![Toolbar popup](./images/popup.gif)

> If the popup content overflows the height of the page, then the rest of the commands will be hidden.

### Priority of commands

Default popup priority is set as `none`, and when the commands of the Toolbar overflow, the ones listed last will be moved to the popup.

You can customize the priority of commands to be displayed on the Toolbar and popup by using the [`overflow`](../api/toolbar/item#overflow) property.

Property     | Description
------------ | -------------
  show       | Always shows items on the `Toolbar with primary` priority.
  hide       | Always shows items in the `popup with secondary` priority.
  none       | No priority display, and as per the `normal order` commands are moved to popup when content exceeds viewing area.

If primary priority commands also exceed available space, they are moved to the popup container at top order position and placed before the secondary priority commands.

> You can maintain toolbar item on popup always by using the [`showAlwaysInPopup`](../api/toolbar/item#showalwaysinpopup) property, and this behavior is not applicable for toolbar items with [`overflow`](../api/toolbar/item#overflow) property as 'show'.

{% tab template="toolbar/toolbar-popup-tool-priority", es5Template="es5_toolbar_tool_priority", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import {Toolbar} from '@syncfusion/ej2-navigations';

let toolbar: Toolbar = new Toolbar({
    width: 380,
    overflowMode: 'Popup',
    items: [
      { type: 'Button', prefixIcon: 'e-cut-icon tb-icons', text:'Cut', overflow: 'Show' },
      { type: 'Button', prefixIcon: 'e-copy-icon tb-icons', text:'Copy', overflow: 'Show' },
      { type: 'Button', prefixIcon: 'e-paste-icon tb-icons',text:'Paste', overflow: 'Show' },
      { type: 'Separator' },
      { type: 'Button', prefixIcon: 'e-bold-icon tb-icons', text:'Bold'},
      { type: 'Button', prefixIcon: 'e-italic-icon tb-icons', text:'Italic'},
      { type: 'Button', prefixIcon: 'e-underline-icon tb-icons', text:'Underline' },
      { type: 'Separator'},
      { type: 'Button', prefixIcon: 'e-ascending-icon tb-icons', text:'A-Z Sort', overflow: 'Show'},
      { type: 'Button', prefixIcon: 'e-descending-icon tb-icons', text:'Z-A Sort', overflow: 'Show'},
      ]
});
toolbar.appendTo('#element');

```

{% endtab %}

### Text mode for buttons

The [`showTextOn`](../api/toolbar/item#showtexton) property is used to decide button text display area on the Toolbar, popup, or both. This is useful for customization of both text and image representation of commands.

For example, you can show icon only button on the Toolbar, and in the popup container display more information about the commands with icon and text.

Possible values are,

  Property   | Description
------------ | -------------
  Both     | Button text is visible in both `Toolbar` and `Popup`.
  Overflow | Button text is only visible in `Popup`.
  Toolbar  | Button text is only visible on the `Toolbar`.

In the following code sample, text is only visible in the popup container and not in the Toolbar container.

{% tab template="toolbar/toolbar-popup-pop-priority", es5Template="es5_toolbar_pop_priority", sourceFiles="index.ts,index.html,index.css" %}

```typescript
import {Toolbar} from '@syncfusion/ej2-navigations';

let toolbar: Toolbar = new Toolbar({
    width: 330,
    overflowMode: 'Popup',
    items: [
      { type: 'Button', prefixIcon: 'e-cut-icon tb-icons', text:'Cut', showTextOn:'Overflow', overflow: 'Show'},
      { type: 'Button', prefixIcon: 'e-copy-icon tb-icons', text:'Copy', showTextOn:'Overflow', overflow: 'Show'},
      { type: 'Button', prefixIcon: 'e-paste-icon tb-icons', text:'Paste', showTextOn:'Overflow', overflow: 'Show'},
      { type: 'Separator'},
      { type: 'Button', prefixIcon: 'e-bold-icon tb-icons', text:'Bold', showTextOn:'Overflow', overflow: 'Show'},
      { type: 'Button', prefixIcon: 'e-underline-icon tb-icons', text:'Underline', showTextOn:'Overflow', overflow: 'Show'},
      { type: 'Button', prefixIcon: 'e-italic-icon tb-icons', text:'Italic', overflow: 'Show', showTextOn:'Overflow',},
      { type: 'Button', prefixIcon: 'e-color-icon tb-icons', text:'Color-Picker', overflow: 'Hide', showTextOn:'Overflow',},
      { type: 'Separator'},
      { type: 'Button', prefixIcon: 'e-ascending-icon tb-icons', text:'A-Z Sort', overflow: 'Show', showTextOn:'Overflow',},
      { type: 'Button', prefixIcon: 'e-descending-icon tb-icons', text:'Z-A Sort', overflow: 'Show', showTextOn:'Overflow',},
      { type: 'Button', prefixIcon: 'e-clear-icon tb-icons', text:'Clear', overflow: 'Show', showTextOn:'Overflow',}]
});
toolbar.appendTo('#element');

```

{% endtab %}