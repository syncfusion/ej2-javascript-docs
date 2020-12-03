---
title: "Dashbaord Layout How To"
component: "Dashboard Layout"
description: "This section explains the dynamically resizing functionality of the Syncfusion JavaScript dashboard layout control."
---

# Dynamically resize the height of panels

In Dashboard Layout, the height of a panel is based on its width. While resizing the panel, the height and width should be changed.

To resize the height of a panel alone, the [resizePanel]( ../../api/dashboard-layout/#resizepanel) method is used. In this case, the [cellAspectRatio](../../api/dashboard-layout/#cellaspectratio) property configures the height of the cells based on the cell width to height ratio (cell width/cell height ratio) when the height will not be completely adjusted to `sizeY` value.

Refer to the following code snippet to determine the height of a panel.

```typescript

let panelContent: HTMLElement = document.getElementById("panelContent");
let panelHeight: number = panelContent.offsetHeight;

```

{% tab template="dashboard-layout/dynamic-resize",sourceFiles="app.ts,index.html,index.css", es5Template="dynamic-resize" %}

```typescript

import { DashboardLayout } from '@syncfusion/ej2-layouts';
import { Button } from '@syncfusion/ej2-buttons';

    let dashboardObject: DashboardLayout = new DashboardLayout({
        cellAspectRatio: 100/70,
        columns: 4,
        panels: [{
            id:'panel0', 'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 0,header: '<div>Panel 0</div>',
            content: '<div class="content" id="panelContent">Place your content here</div>'
        },
        {
            id:'panel1', 'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 1,
            header: '<div>Panel 1</div>',
            content: '<div class="content" id="panelContent">Place your content here</div>'
        },
        {
            id:'panel2', 'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 2,
            header: '<div>Panel 2</div>',
            content: '<div class="content" id="panelContent">Place your content here</div>'
        }]
    });
    dashboardObject.appendTo('#defaultLayout');

    let btnInstance: Button = new Button({cssClass:"e-outline e-success"});
    btnInstance.appendTo('#editbtn');

    btnInstance.element.onclick = () => {
      let panelContent: HTMLElement = document.getElementById("panelContent");
      let panelHeight: number  = panelContent.offsetHeight;
      let panelWidth: number = panelContent.offsetWidth;
      let diff: number = Math.round(panelHeight/panelWidth);
      dashboardObject.resizePanel('panel0', 1, diff);
      dashboardObject.resizePanel('panel1', 1, diff);
      dashboardObject.resizePanel('panel2', 1, diff);
    };

```

{% endtab %}
