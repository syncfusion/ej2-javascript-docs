# Align multiple sidebar in same position

You can initialize Sidebar at the left positions by using the [`position`](../../api/sidebar/#position) property. It will automatically adjust the width of the main content.

You can also initialize the another sidebar on the same position by adjusting the width of the first sidebar.

The following example demonstrate how to align the multiple sidebar on the same position.

{% tab template="sidebar/sidebar-same-position", es5Template="sidebar-same-position", isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

//Dock Sidebar initialization
let dockBar: Sidebar = new Sidebar({
        width: '220px',
        dockSize: '72px',
        enableDock: true,
        type:'Push',
        target:'e-main-content',
        zIndex:3000
});
dockBar.appendTo('#dockSidebar');
//end of DockSidebar initialization

let defaultSidebar: Sidebar = new Sidebar({
      target:'e-main-content',
      type:"Push",
 });
defaultSidebar.appendTo('#default-sidebar');
//end of DefaultSidebar initialization

//switch the expand and collapse state
    document.getElementById('buttonClick').onclick = function () {
        defaultSidebar.toggle();
    };

```

{% endtab %}