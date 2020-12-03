# Template

## Render UL and LI template

Add the HTML UL tag with `id` attribute as `#contextmenu` in your `index.html` file with required LI tags and also add target element on which the ContextMenu has to be opened.

{% tab template= "context-menu/how-to/ultemplate", sourceFiles="app.ts,index.html,styles.css",
es5Template="ul-li-template" %}

```typescript
import { ContextMenu } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
// To Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu({ target: '#target' }, '#contextmenu');

```

{% endtab %}

## Show table in sub ContextMenu

Menu items of the ContextMenu can be customized according to the requirement. The section explains about how to customize table template
in sub menu item.

This can be achieved by appending table layout while `li` rendering by using [`beforeItemRender`](../api/context-menu#beforeitemrender) event.

{% tab template= "context-menu/table", sourceFiles="app.ts,index.html,styles.css",
es5Template="table-template" %}

```typescript
import { Browser } from '@syncfusion/ej2-base';
import { ContextMenu, MenuEventArgs, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// To create header element.
let header: HTMLElement = document.createElement('h4');
header.textContent = 'Insert Table';

// To create table with five rows and six columns.
let table: HTMLElement = document.createElement('table');
for (let i: number = 0; i < 5; i++) {
    let row: HTMLElement = document.createElement('tr');
    table.appendChild(row);
for (let j: number = 0; j < 6; j++) {
    let col: HTMLElement = document.createElement('td');
    row.appendChild(col);
    col.setAttribute('class', 'e-border');
}
}

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Cut',
        iconCss: 'e-cm-icons e-cut'
    },
    {
        text: 'Copy',
        iconCss: 'e-icons e-copy'
    },
    {
        text: 'Paste',
        iconCss: 'e-cm-icons e-paste'
    },
    {
        separator: true
    },
    {
        text: 'Link',
        iconCss: 'e-icons e-link'
    },
    {
        text: 'Table',
        iconCss: 'e-icons e-table',
        items: [
            {
              id: 'table'
            }
        ]
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
    target: '#target',
    items: menuItems,
    beforeItemRender: (args: MenuEventArgs) => {
      // To append table on `li` rendering.
      if (args.item.id === 'table') {
        args.element.classList.add('bg-transparent');
        args.element.appendChild(header);
        args.element.appendChild(table);
      }
    }
};

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');
```

{% endtab %}

## Show UI components in ContextMenu

UI components can also be placed inside the each `li` element of ContextMenu.

In the following example, CheckBox component is placed inside each `li` element and this can be achieved by creating
CheckBox component in [`beforeItemRender`](../api/context-menu#beforeitemrender) event and appending it into the `li` element.

{% tab template= "context-menu/ui-component", sourceFiles="app.ts,index.html,styles.css",
es5Template="ui-template" %}

```typescript
import { closest, enableRipple} from '@syncfusion/ej2-base';
import { ContextMenu, MenuEventArgs, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { ContextMenuModel, MenuItemModel } from '@syncfusion/ej2-navigations';
import { CheckBox } from '@syncfusion/ej2-buttons';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    { text: 'Option 1' },
    { text: 'Option 2' },
    { text: 'Option 3' }
];

let i = 1;
// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
    target: '#target',
    items: menuItems,
    beforeItemRender: (args: MenuEventArgs) => {
        // To render CheckBox component on each li.
        let checkbox: CheckBox = new CheckBox({ label: 'Option'+  i, checked: i%2 === 0 ? true : false });
        args.element.innerHTML = '';
        checkbox.appendTo('#checkbox'+i);
        let checkboxObj = document.getElementsByClassName('e-checkbox-wrapper');
        args.element.appendChild(checkboxObj[0]);
        i++;
    },
    beforeClose: (args: BeforeOpenCloseMenuEventArgs) => {
        if ((args.event.target as HTMLElement).closest('.e-menu-item')) {
            // To prevent ContextMenu close on item click.
            args.cancel = true;
        }
    },
    select: (args: MenuEventArgs) => {
        let selectedElem: NodeList = args.element.parentElement.querySelectorAll('.e-selected');
        for (let i:number=0; i < selectedElem.length; i++) {
           let ele: Element = selectedElem[i] as Element;
           ele.classList.remove('e-selected');
        }
        let checkbox: HTMLElement = args.element.childNodes[0] as HTMLElement;
        let frame: Element = checkbox.querySelector('.e-frame');
        if (checkbox && frame.classList.contains('e-check')) {
            frame.classList.remove('e-check');
        } else if (checkbox) {
            frame.classList.add('e-check');
        }
    }
};

let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');
```

{% endtab %}
