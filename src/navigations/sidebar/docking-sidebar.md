---
title: "Docking Sidebar"
component: "Sidebar"
description: "Docking lets the sidebar occupy a small vertical area in a page always and typically contains shortened view of navigation options."
---

# Dock

[`Dock`](../api/sidebar/#enabledock) state of the Sidebar reserves some space on the page that always remains in a visible state when the Sidebar is collapsed. It is used to show the short term of a content like icons alone instead of lengthy text. To achieve this , set `enableDock` as true along with required `dockSize`.

In the following sample, the list item has icon with text representation. On dock state, only icons in list will be visible to represent the hint of the hidden text content.

{% tab template="sidebar/sidebar-dock", es5Template="es5_sidebar_dock" ,isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css"%}

```typescript
import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(false);

//Sidebar initialization
let dockBar: Sidebar = new Sidebar({
    width: '220px',
    dockSize: '72px',
    enableDock: true
});

dockBar.appendTo('#dockSidebar');
//end of Sidebar initialization

document.getElementById('toggle').onclick = (): void => {
    dockBar.toggle();
};

```

{% endtab %}

## See Also

* [How to add sidebar navigation](./how-to/sidebar-with-treeview)