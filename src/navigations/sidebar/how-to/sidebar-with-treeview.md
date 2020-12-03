---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Initialize the Sidebar with TreeView

The following example demonstrates how to render TreeView component inside the Sidebar with dock state and how to achieve expand and collapse the functionalities simultaneously in the sidebar and Treeview.

On collapse, the LI elements of TreeView show icons only to represent the short sign of the hidden text content. On expand, hidden text content will be set to be visible.

{% tab template="sidebar/sidebar-treeview", es5Template="es5_sidebar_treeview", isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar, TreeView } from '@syncfusion/ej2-navigations';
import { ListView } from '@syncfusion/ej2-lists';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

let sidebarMenu: Sidebar = new Sidebar({
    width: '290px',
    dockSize:"44px",
    enableDock: true,
    target: '.main-content',
    mediaQuery: '(min-width: 600px)',
    created:onCreate,
    close: onClose
});
sidebarMenu.appendTo('#sidebar-treeview');


let data: { [key: string]: Object }[] = [
       {
            nodeId: '01', nodeText: 'Installation', iconCss: 'icon-microchip icon',
            nodeChild: [
                { nodeId: '05-01', nodeText: 'Calendar', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-02', nodeText: 'DatePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-03', nodeText: 'DateTimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-04', nodeText: 'DateRangePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-05', nodeText: 'TimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-06', nodeText: 'SideBar', iconCss: 'icon-circle-thin icon' }
            ]
        },
        {
            nodeId: '02', nodeText: 'Deployment', iconCss: 'icon-thumbs-up-alt icon',
        },
        {
            nodeId: '03', nodeText: 'Quick Start', iconCss: 'icon-docs icon',
        },
        {
            nodeId: '04', nodeText: 'Components', iconCss: 'icon-th icon',
            nodeChild: [
                { nodeId: '04-01', nodeText: 'Calendar', iconCss: 'icon-circle-thin icon' },
                { nodeId: '04-02', nodeText: 'DatePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '04-03', nodeText: 'DateTimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '04-04', nodeText: 'DateRangePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '04-05', nodeText: 'TimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '04-06', nodeText: 'SideBar', iconCss: 'icon-circle-thin icon' }
            ]
        },
        {
            nodeId: '05', nodeText: 'API Reference', iconCss: 'icon-code icon',
            nodeChild: [
                { nodeId: '05-01', nodeText: 'Calendar', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-02', nodeText: 'DatePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-03', nodeText: 'DateTimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-04', nodeText: 'DateRangePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-05', nodeText: 'TimePicker', iconCss: 'icon-circle-thin icon' },
                { nodeId: '05-06', nodeText: 'SideBar', iconCss: 'icon-circle-thin icon' }
            ]
        },
        {
            nodeId: '06', nodeText: 'Browser Compatibility', iconCss: 'icon-chrome icon'
        },
        {
            nodeId: '07', nodeText: 'Upgrade Packages', iconCss: 'icon-up-hand icon'
        },
        {
            nodeId: '08', nodeText: 'Release Notes', iconCss: 'icon-bookmark-empty icon'
        },
        {
            nodeId: '09', nodeText: 'FAQ', iconCss: 'icon-help-circled icon'
        },
        {
            nodeId: '10', nodeText: 'License', iconCss: 'icon-doc-text icon'
        }
];

// TreeView  initialization
let mainTreeView: TreeView = new TreeView({
    fields: { dataSource: data, id: 'nodeId', text: 'nodeText', child: 'nodeChild' }, expandOn: 'Click',
});

mainTreeView.appendTo('#main-treeview');

document.getElementById('hamburger').onclick = (): void => {  
    if(sidebarMenu.isOpen)
    {
        sidebarMenu.hide();
        mainTreeView.collapseAll();
    }
    else {
        sidebarMenu.show();
        mainTreeView.expandAll();
    }
};
function onCreate(): void {
    this.element.style.visibility = '';
}
function onClose(args: any) {
    mainTreeView.collapseAll();
}


```

{% endtab %}
