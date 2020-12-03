---
title: "Floating"
component: "Dashboard Layout"
description: "This section explains the floating functionality of Essential JS 2 DashboardLayout component"
---

# Floating

The floating functionality of the component allows to effectively use the entire layout for the panel's placement. If the floating functionality is enabled, the panels within the layout get floated upwards automatically to occupy the empty cells available in previous rows. This functionality can be enabled or disabled using the [`allowFloating`](../api/dashboard-layout/#allowfloating) property of the component.

The following sample demonstrates how to enable or disable the floating of panels in the DashboardLayout component.

{% tab template="dashboard-layout/floating",sourceFiles="app.ts,index.html,index.css", es5Template="floating" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';
import { Button } from '@syncfusion/ej2-buttons';

// initialize dashboardlayout component
let dashboard: DashboardLayout = new DashboardLayout({
    cellSpacing: [10, 10],
    allowFloating: false,
    cellAspectRatio: 100 / 75,
    columns: 6,
    panels: [{ 'sizeX': 2, 'sizeY': 2, 'row': 1, 'col': 0, content: '<div class="content">0</div>' },
    { 'sizeX': 2, 'sizeY': 2, 'row': 2, 'col': 2, content: '<div class="content">1</div>' },
    { 'sizeX': 2, 'sizeY': 2, 'row': 3, 'col': 4, content: '<div class="content">2</div>' }]
});
// render initialized dashboardlayout
dashboard.appendTo('#dashboard_default');

let resetPanels = dashboard.serialize();
resetPanels[0].content = '<div class="content">0</div>';
resetPanels[1].content = '<div class="content">1</div>';
resetPanels[2].content = '<div class="content">2</div>';

let toggleBtn: Button = new Button({
    cssClass: "e-flat e-primary e-outline",
    content: "Enable Floating",
    isToggle: true
});
toggleBtn.appendTo("#toggle");

document.getElementById('toggle').onclick = () => {
    let panels = [];
    if (toggleBtn.content == "Disable Floating and Reset") {
        toggleBtn.content = 'Enable Floating';
        dashboard.allowFloating = false;
        dashboard.panels = resetPanels;
    } else {
        toggleBtn.content = 'Disable Floating and Reset';
        dashboard.allowFloating = true;
    }
};

```

{% endtab %}