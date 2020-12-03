---
title: "Resizing panels"
component: "Dashboard Layout"
description: "This section explains how to enable resizing and the dynamic resizing of panels within the layout in Essential JS 2 DashboardLayout component"
---

# Resizing panels

The DashboardLayout component is also provided with the panel resizing functionality which can be enabled or disabled using the [`allowResizing`](../../api/dashboard-layout/#allowresizing) property. This functionality allows to resize the panels dynamically through UI interactions using the resizing handlers which controls the panel resizing in various directions.

Initially, the panels can be resized only in south-east direction. However, panels can also be resized in east, west, north, south and south-west directions by defining the required directions with [`resizableHandles`](../../api/dashboard-layout/#resizablehandles) property.

On resizing a panel in Dashboard layout the following events will be triggered,
* [resizeStart](../../api/dashboard-layout/#resizestart) - Triggers when panel resize starts
* [resize](../../api/dashboard-layout/#resize) - Triggers when panel is being resized
* [resizeStop](../../api/dashboard-layout/#resizestop) - Triggers when panel resize stops

The following sample demonstrates how to enable and disable the resizing of panels in the DashboardLayout component in different directions.

{% tab template="dashboard-layout/resizing",sourceFiles="app.ts,index.html,index.css", es5Template="resizing" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';

// initialize dashboardlayout component
let dashboard: DashboardLayout = new DashboardLayout({
    cellSpacing: [10, 10],
    allowResizing: true,
    columns: 5,
      //Dashboard Layout's resizestart event
    resizeStart: onResizeStart,
    //Dashboard Layout's resize event
    resize: onResize,
    //Dashboard Layout's resizestop event
    resizeStop: onResizeStop,
    resizableHandles: ['e-south-east','e-east','e-west','e-north','e-south'],
    panels: [{ 'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 0, content: '<div class="content">0</div>' },
    { 'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 1, content: '<div class="content">1</div>' },
    { 'sizeX': 1, 'sizeY': 3, 'row': 0, 'col': 4, content: '<div class="content">2</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 1, 'col': 0, content: '<div class="content">3</div>' },
    { 'sizeX': 2, 'sizeY': 1, 'row': 2, 'col': 0, content: '<div class="content">4</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 2, content: '<div class="content">5</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 3, content: '<div class="content">6</div>' }]
});
// render initialized dashboardlayout
dashboard.appendTo('#dashboard_default');
//Dashboard Layout's resizestart event function
function onResizeStart(args: any) {
    console.log("Resize start");
}

//Dashboard Layout's resize event function
function onResize(args: any) {
    console.log("Resizing");
}

//Dashboard Layout's resizestop event function
function onResizeStop(args: any) {
    console.log("Resize stop");
}
```

{% endtab %}

# Resizing panels programatically

The Dashboard Layout panels can also be resized programatically by using [resizePanel](../../api/dashboard-layout/#resizepanel) method. The method is invoked as follows,

```js
resizePanel(id, sizeX, sizeY)

```

Where,
* id - ID of the panel which needs to be resized.
* sizeX - New panel width in cells count for resizing the panel.
* sizeY - New panel height in cells count for resizing the panel.

The following sample demonstrates resizing panels programatically in the Dashboard Layout's [created](../../api/dashboard-layout/#created) event.

{% tab template="dashboard-layout/resize-panel",sourceFiles="app.ts,index.html,index.css", es5Template="resize-panel" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';

// initialize dashboardlayout component
let dashboard: DashboardLayout  = new DashboardLayout({
    cellSpacing: [10, 10],
    columns: 5,
    //Dashboard Layout's created event
    created: onCreated,
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
    // resizePanel("id", sizeX, sizeY)
    this.resizePanel("layout_4", 1, 1);
    this.resizePanel("layout_5", 2, 1);
}
```

{% endtab %}
