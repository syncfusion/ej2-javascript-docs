---
title: "Dragging and moving of panels"
component: "Dashboard Layout"
description: "This section explains how to adjust the panels within the layout in Essential JS 2 Dashboard Layout component"
---

# Dragging of panels

The Dashboard Layout component is provided with dragging functionality to drag and reorder the panels within the layout. While dragging a panel, a holder will be highlighted below the panel indicating the panel placement on panel drop. This helps the user to decide whether to place the panel in the current position or revert to previous position without disturbing the layout.

If one or more panels collide while dragging, then the colliding panels will be pushed towards left or right or top or bottom direction where an adaptive space for the collided panel is available. The position changes of these collided panels will be updated dynamically during dragging of a panel so the user can conclude whether to place the panel in the current position or not.

While dragging a panel in Dashboard layout the following dragging events will be triggered,
* [dragStart](../../api/dashboard-layout/#dragstart) - Triggers when panel drag starts
* [drag](../../api/dashboard-layout/#drag) - Triggers when panel is being dragged
* [dragStop](../../api/dashboard-layout/#dragstop) - Triggers when panel drag stops

The following sample demonstrates dragging and pushing of panels. Here, for e.g. While dragging the panel 0 over panel 1, these panels get collided and push the panel 1 towards the feasible direction so that panel 0 gets placed in the panel 1 position.

{% tab template="dashboard-layout/sizing-of-cells",sourceFiles="app.ts,index.html,index.css", es5Template="dragging" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';

// initialize dashboardlayout component
let dashboard: DashboardLayout = new DashboardLayout({
    cellSpacing: [10, 10],
    columns: 5,
     //Dashboard Layout's dragstart event
    dragStart: onDragStart,
    //Dashboard Layout's drag event
    drag: onDrag,
    //Dashboard Layout's dragstop event
    dragStop: onDragStop,
    panels: [{ 'sizeX': 1, 'sizeY': 1, 'row': 0, 'col': 0, content: '<div class="content">0</div>' },
    { 'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 1, content: '<div class="content">1</div>' },
    { 'sizeX': 1, 'sizeY': 3, 'row': 0, 'col': 4, content: '<div class="content">2</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 1, 'col': 0, content: '<div class="content">3</div>' },
    { 'sizeX': 2, 'sizeY': 1, 'row': 2, 'col': 0, content: '<div class="content">4</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 2, content: '<div class="content">5</div>' },
    { 'sizeX': 1, 'sizeY': 1, 'row': 2, 'col': 3, content: '<div class="content">6</div>' }]
});
// render initialized dashboardlayout
dashboard.appendTo('#dashboard_layout');
//Dashboard Layout's dragstart event function
function onDragStart(args: any) {
    console.log("Drag start");
}

//Dashboard Layout's drag event function
function onDrag(args: any) {
    console.log("Dragging");
}

//Dashboard Layout's dragstop event function
function onDragStop(args: any) {
    console.log("Drag stop");
}
```

{% endtab %}

# Customizing the dragging handler

Initially, the complete panel will act as the handler for dragging the panel such that the dragging action occurs on clicking anywhere over a panel. However, this dragging handler for the panels can be customized using the [`draggableHandle`](../../api/dashboard-layout/#draggablehandle) property to restrict the dragging action within a particular element in the panel.

The following sample demonstrates customizing the dragging handler of the panels where dragging action of panel occurs only with the header of the panel.

{% tab template="dashboard-layout/drag_handler",sourceFiles="app.ts,index.html,index.css", es5Template="handler" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';
import { Chart, ColumnSeries, Category, LineSeries, AccumulationChart, AccumulationTooltip, PieSeries } from '@syncfusion/ej2-charts';
Chart.Inject(ColumnSeries, Category, LineSeries);
AccumulationChart.Inject(AccumulationTooltip, PieSeries);

// initialize dashboardlayout component
let dashboard: DashboardLayout = new DashboardLayout({
    cellSpacing: [10, 10],
    columns: 6,
    draggableHandle: '.e-panel-header',
    panels: [{ 'id': 'Panel1', 'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 0, header: '<div class="header"> Product usage ratio </div><span class="handler e-icons burg-icon"></span>', content: '<div id="pie"><div>' },
    { 'id': 'Panel2', 'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 3, header: '<div class="header"> Last year Sales Comparison </div> <span class="handler e-icons burg-icon"></span>', content: '<div id="column"><div>' },
    { 'id': 'Panel3', 'sizeX': 3, 'sizeY': 2, 'row': 0, 'col': 3, header: '<div class="header"> Mobile browsers usage </div><span class="handler e-icons burg-icon"></span>', content: '<div id="pie1"><div>' },
    { 'id': 'Panel4', 'sizeX': 3, 'sizeY': 2, 'row': 1, 'col': 0, header: '<div class="header"> Sales increase percentage </div><span class="handler e-icons burg-icon"></span>', content: '<div id="line"><div>' }
    ]
});
// render initialized dashboardlayout
dashboard.appendTo('#dashboard_default');

let chartData: any[] = [
    { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
    { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
    { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
    { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
    { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
    { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
let chart: Chart = new Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series: [{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Column'
    }],
    height: "162px"
}, '#column');

let lineData: any[] = [
    { x: 2013, y: 28 }, { x: 2014, y: 25 }, { x: 2015, y: 26 }, { x: 2016, y: 27 },
    { x: 2017, y: 32 }, { x: 2018, y: 35 },
];
let linechart: Chart = new Chart({
    series: [{
        dataSource: lineData,
        xName: 'x', yName: 'y',
        //Series type as line
        type: 'Line'
    }],
    height: "162px"
}, '#line');

let accChart: AccumulationChart = new AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'TypeScript', y: 13, text: 'TS 13%' }, { x: 'React', y: 12.5, text: 'Reat 12.5%' }, { x: 'MVC', y: 12, text: 'MVC 12%' }, { x: 'Core', y: 12.5, text: 'Core 12.5%' }, { x: 'Vue', y: 10, text: 'Vue 10%' }, { x: 'Angular', y: 40, text: 'Angular 40%' }],
            xName: 'x',
            yName: 'y',
            innerRadius: "20%"
        }],
    tooltip: { enable: true },
    height: "162px"
}, '#pie');

let piechart: AccumulationChart = new AccumulationChart({
    // Initialize the chart series
    series: [
        {
            dataSource: [
                { 'x': 'Chrome', y: 37, text: '37%' }, { 'x': 'UC Browser', y: 17, text: '17%' },
                { 'x': 'iPhone', y: 19, text: '19%' },
                { 'x': 'Others', y: 4, text: '4%' }, { 'x': 'Opera', y: 11, text: '11%' },
                { 'x': 'Android', y: 12, text: '12%' }
            ],
            dataLabel: {
                visible: true, position: 'Inside', name: 'text', font: { fontWeight: '600' }
            },
            radius: '70%', xName: 'x', yName: 'y', name: 'Browser'
        }
    ],
    center: { x: '50%', y: '50%' },
    enableSmartLabels: true,
    height: "162px",
    enableAnimation: false,
    legendSettings: { visible: false },
    // Initialize tht tooltip
    tooltip: { enable: true, format: '${point.x} : <b>${point.y}%</b>' },

}, '#pie1');

```

{% endtab %}

# Disable dragging of panels

By default, the dragging of panels is enabled in Dashboard Layout. It can also be disabled with the help of [allowDragging](../../api/dashboard-layout/#allowdragging) API. Setting [allowDragging](../../api/dashboard-layout/#allowdragging) to false disables the dragging functionality in Dashboard Layout.

The following sample demonstrates Dashboard Layout with dragging support disabled.

{% tab template="dashboard-layout/disable-dragging",sourceFiles="app.ts,index.html,index.css", es5Template="disable-dragging" %}

```typescript
import { DashboardLayout } from '@syncfusion/ej2-layouts';

// initialize dashboardlayout component
let dashboard: DashboardLayout  = new DashboardLayout({
    cellSpacing: [10, 10],
    allowDragging: false,
    columns: 5,
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
```

{% endtab %}