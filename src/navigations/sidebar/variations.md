---
title: "Variatons"
component: "Sidebar"
description: "The different types in type property of the sidebar gives flexibility to view or hide the content (primary/secondary) over/above the main content by pushing, sliding, or overlaying it."
---

# Types

The Sidebar component's expand behaviour can be modified based on the purpose of use.

## Expanding types of Sidebar

The Sidebar can be set to initialize based on four different types that are consistent with the main component as explained below. When `dataBind` is invoked, this applies the pending property changes immediately to the component.

 | Item | Description |
|-----|-----|
| `Over` | Sidebar floats over the main content area.|
| `Push` | Sidebar pushes the main content area to appear side-by-side, and shrinks the main content within the screen width.|
| `Slide` |Sidebar translates the x and y positions of main content area based on the Sidebar width. The main content area will not be adjusted within the screen width. |
| `Auto` | Sidebar with `Over` type in mobile resolution, and `Push` type in other higher resolutions. |

> `Auto` is the default expand mode. Sidebar with type `Auto` will always expand on initial rendering, irrespective of [`enableDock`](../api/sidebar/#enabledock) and [`isOpen`](../api/sidebar/#isopen) properties.

In the following sample, the types of Sidebar are demonstrated.

{% tab template="sidebar/types", es5Template="es5_sidebar_multiple", sourceFiles="app.ts,index.html,styles.css"%}

```typescript
import { Sidebar } from '@syncfusion/ej2-navigations';
import { Button,RadioButton, ChangeArgs } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

let defaultSidebar: Sidebar = new Sidebar({
    type: "Push",
    target: <HTMLElement>document.querySelector('.maincontent'),
});
defaultSidebar.appendTo('#default-sidebar');
//end of Sidebar initialization

//toggle button initialization
let togglebtn: Button = new Button({iconCss: 'e-icons burg-icon', isToggle: true, content:'Open'}, '#toggle');

//Click Event.
document.getElementById('toggle').onclick = (): void => {
        if (document.getElementById('toggle').classList.contains('e-active')) {
            togglebtn.content = 'Close';
            defaultSidebar.show();
        } else {
            togglebtn.content = 'Open';
            defaultSidebar.hide();
        }
    };

// Close the Sidebar
document.getElementById('close').onclick = (): void => {
    defaultSidebar.hide();
    document.getElementById('toggle').classList.remove('e-active');
    togglebtn.content = 'Open'
};

let typeOver: RadioButton = new RadioButton({ label: 'Over', name: 'state', change: Change });
typeOver.appendTo('#over');

//unchecked state.
let typePush: RadioButton = new RadioButton({ label: 'Push', name: 'state', checked: true, change: Change });
typePush.appendTo('#push');

let typeSlide: RadioButton = new RadioButton({ label: 'Slide', name: 'state', change: Change });
typeSlide.appendTo('#slide');

//unchecked state.
let typeAuto: RadioButton = new RadioButton({ label: 'Auto', name: 'state', change: Change });
typeAuto.appendTo('#auto');

//change the togglebtn state.
function Changestate() {
    if (defaultSidebar.type == "Auto") {
        document.getElementById('toggle').classList.add('e-active');
        togglebtn.content = 'close';
    }
    else {
        document.getElementById('toggle').classList.remove('e-active');
        togglebtn.content = 'Open';
    }
}

function Change(args: ChangeArgs) {
    if ((<HTMLInputElement>args.event.target).id == "over") {
        defaultSidebar.type = "Over";
    } else if ((<HTMLInputElement>args.event.target).id == "push") {
        defaultSidebar.type = "Push";
    }
    else if ((<HTMLInputElement>args.event.target).id == "slide") {
        defaultSidebar.type = "Slide";
    }
    else {
        defaultSidebar.type = "Auto";
    }
    Changestate();
    defaultSidebar.dataBind();
}
```

{% endtab %}

## See Also

* [How to add sidebar with custom animation](./how-to/sidebar-with-variation-animation)
* [How to add multiple sidebar](./how-to/multiple-sidebar)
