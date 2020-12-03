# Customize menu using events

The Menu provides a set of [`events`](../../api/menu#events) to enable users to customize it.

The available events are [`beforeOpen`](../../api/menu/#beforeclose), [`beforeClose`](../..api//menu/#beforeopen), [`onClose`](../../api/menu/#onclose), [`onOpen`](../../api/menu/#onopen), and [`select`](../..api//menu/#select).

{% tab template="menu/handle-event", sourceFiles="app.ts,index.html,styles.css",
 es5Template="icons-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel, MenuEventArgs } from '@syncfusion/ej2-navigations';
import { OpenCloseMenuEventArgs, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu items definition
let menuItems: MenuItemModel[] = [
    {
        text: 'Events',
        items: [
            { text: 'Conferences' },
            { text: 'Music' },
            { text: 'Workshops' }
        ]
    },
    {
        text: 'Movies',
        items: [
            { text: 'Now Showing' },
            { text: 'Coming Soon' }
        ]
    },
    {
        text: 'Directory',
        items: [
            { text: 'Media Gallery' },
            { text: 'Newsletters' }
        ]
    },
    {
        text: 'Queries',
        items: [
            { text: 'Our Policy' },
            { text: 'Site Map' }
        ]
    },
    { text: 'Services' }
];

// Initialize Menu component.
let menuObj: Menu = new Menu({
    items: menuItems,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
        updateEventLog(args);
    },
    beforeClose: (args: BeforeOpenCloseMenuEventArgs) => {
        updateEventLog(args);
    },
    onClose: (args: OpenCloseMenuEventArgs) => {
        updateEventLog(args);
    },
    onOpen: (args: OpenCloseMenuEventArgs) => {
        updateEventLog(args);
    },
    select: (args: MenuEventArgs) => {
        updateEventLog(args);
    }
}, '#menu');

let clear: Button = new Button({ cssClass: 'e-small'});
clear.appendTo('#clear');

clear.element.onclick = () => {
    let propertyElem: HTMLElement = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].innerHTML = '';
}

function updateEventLog(args: any): void {
    let propertyElem: HTMLElement = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].insertAdjacentHTML('beforeend', args.name + ' Event triggered. <br />');
}
```

{% endtab %}
