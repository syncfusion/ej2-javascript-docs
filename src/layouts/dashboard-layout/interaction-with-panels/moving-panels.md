---
title: "Moving of panels programatically"
component: "Dashboard Layout"
description: "This section explains how to move the panels programatically within the layout in Essential JS 2 Dashboard Layout component"
---

# Moving of panels programatically

Other than drag and drop, it is possible to move the panels in Dashboard Layout programatically. This can be achieved using [movePanel](../../api/dashboard-layout/#movepanel) method. The method is invoked as follows,

```js
movePanel(id, row, col)

```

Where,
* id - ID of the panel which needs to be moved.
* row - New row position for moving the panel.
* col - New column position for moving the panel.

Each time a panel's position is changed(Programatically or through UI interaction), the Dashboard Layout's [change](../../api/dashboard-layout/#change) event will be triggered.

The following sample demonstrates moving a panel programatically to a new position in the Dashboard Layout's [created](../../api/dashboard-layout/#created) event.

{% tab template="dashboard-layout/moving",sourceFiles="app.ts,index.html,index.css", es5Template="move-panel" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';

// initialize dashboardlayout component
let dashboard: DashboardLayout  = new DashboardLayout({
    cellSpacing: [10, 10],
    columns: 5,
    //Dashboard Layout's created event
    created: onCreated,
    //Dashboard Layout's change event
    change: onChange,
    panels: [{'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 0, content:'<div class="content">0</div>'},
    {'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 1, content:'<div class="content">1</div>'},
    {'sizeX': 1, 'sizeY': 3, 'row': 0, 'col': 4, content:'<div class="content">2</div>'},
    {'sizeX': 1, 'sizeY': 1, 'row': 1, 'col': 0, content:'<div class="content">3</div>'},
    {'sizeX': 2, 'sizeY': 1, 'row': 2, 'col': 0, content:'<div class="content">4</div>'},
    {'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 2, content:'<div class="content">5</div>'},
    {'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 3, content:'<div class="content">6</div>'}]
    });
// render initialized dashboardlayout
dashboard.appendTo('#dashboard_layout');

//Dashboard Layout's created event function
function onCreated(args: any) {
    // movePanel("id", row, col)
    this.movePanel("layout_0", 1, 0);
}

//Dashboard Layout's change event function
function onChange(args: any) {
    console.log("Change event triggered");
}
```

{% endtab %}