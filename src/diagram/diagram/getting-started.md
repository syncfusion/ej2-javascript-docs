---
title: "Getting Started"
component: "Diagram"
description: "Diagram getting started creates your first flow diagram and organizational chart diagram."
---

# Getting Started

This section explains the steps required to create a simple diagram and demonstrates the basic usage of the diagram control.

<!-- markdownlint-disable MD033 -->

## Dependencies

The following list of dependencies are required to use the `Diagram` component in your application.

```javascript
|-- @syncfusion/ej2-diagrams
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-splitbuttons
```

## Installation and Configuration

* To get started with the diagram component, clone the [`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

* `Diagram packages` should be mapped in the `system.config.js` configuration file.

```javascript
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-diagrams": "syncfusion:ej2-diagrams/dist/ej2-diagrams.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common settings (`src/styles/styles.css`, `system.config.js`) to start with all Essential JS 2 components.

## Add diagram to the project

Add the HTML div element for the diagram into your `index.html`. `[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>EJ2 Diagram</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Typescript UI Controls" />
    <meta name="author" content="Syncfusion" />
    <link href="index.css" rel="stylesheet" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.19.38/system.js"></script>
    <script src="systemjs.config.js"></script>
</head>

<body>
     <!--container which is going to render the Diagram-->
     <div id='container'>
     </div>
</body>

</html>
```

Now, import the diagram component into your `app.ts` to instantiate a diagram and append the diagram instance to the `#container`. `[src/app/app.ts]`

The following example shows a basic diagram.

{% tab template= "diagram/getting-started", es5Template="es5default" %}

```typescript

import { Diagram } from '@syncfusion/ej2-diagrams';

let diagram: Diagram = new Diagram({
    width: '100%', height: '600px'
});
diagram.appendTo('#element');

```

{% endtab %}

Now, the `npm run start` command is used to run the application in the browser.

```cmd

npm run start

```

## Module Injection

The diagram component is divided into individual feature-wise modules. In order to use a particular feature, inject the required module. The following list describes the module names and their description.

* `BpmnDiagrams`: Inject this provider to add built-in BPMN shapes to diagrams.
* `ConnectorBridging`: Inject this provider to add bridges to connectors.
* `ConnectorEditing`: Inject this provider to edit the segments for connector.
* `ComplexHierarchicalTree`: Inject this provider to complex hierarchical tree like structure.
* `DataBinding`: Inject this provider to populate nodes from given data source.
* `DiagramContextMenu`: Inject this provider to manipulate context menu.
* `HierarchicalTree`: Inject this provider to use hierarchical tree like structure.
* `LayoutAnimation`: Inject this provider animation to layouts.
* `MindMap`: Inject this provider to use mind map.
* `PrintAndExport`: Inject this provider to print or export the objects.
* `RadialTree`: Inject this provider to use radial tree like structure.
* `Snapping`: Inject this provider to snap the objects.
* `SymmetricLayout`: Inject this provider to render layout in symmetrical method.
* `UndoRedo`: Inject this provider to revert and restore the changes.

These modules should be imported and injected into the Diagram component using `Diagram.Inject` method as follows.

```javascript
import { Diagram, HierarchicalTree, MindMap, RadialTree, ComplexHierarchicalTree, DataBinding, Snapping, PrintAndExport, BpmnDiagrams, SymmetricLayout, ConnectorBridging, UndoRedo, LayoutAnimation, DiagramContextMenu, ConnectorEditing } from '@syncfusion/ej2-diagrams';

Diagram.Inject(BpmnDiagrams, ConnectorBridging, ConnectorEditing, ComplexHierarchicalTree, DataBinding, DiagramContextMenu, HierarchicalTree, LayoutAnimation, MindMap, PrintAndExport, RadialTree, Snapping, SymmetricLayout, UndoRedo);
```

## Flow Diagram

### Create and add node

Create and add a `node` (JSON data) with specific position, size, label, and shape.

{% tab template= "diagram/getting-started", es5Template="es5Node" %}

```typescript

import { Diagram, NodeModel } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.

let nodes: NodeModel[] = [{
    // Unique name for the node
    name: "Start",
    // Position of the node
    offsetX: 300,
    offsetY: 50,
    // Size of the node
    width: 140,
    height: 50,
    // Text(label) added to the node
    annotations: [{
        id: 'label1',
        content: 'Start'
        }],
        // Shape for the node
        shape: { type: 'Flow', shape: 'Terminator'}
        }
        ];

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%', height: '600px',
    // Add node
    nodes: nodes
});
// render initialized Diagram
diagram.appendTo('#element');

```

{% endtab %}

>Note: The `annotations` property is an array, which indicates that more than one label can be added to a node.

### Connect Nodes

Add two node to the diagram as shown in the previous example. Connect these nodes by adding a connector using the `connector` property and refer the source and target end by using the `sourceNode` and `tagetNode` properties.

{% tab template= "diagram/getting-started", es5Template="es5Connect" %}

```typescript

import { Diagram, NodeModel, ConnectorModel } from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [
    {
        id: 'Start', width: 140, height: 50, offsetX: 300, offsetY: 50,
        annotations: [{
            id: 'label1',
            content: 'Start'
        }],
        shape: { type: 'Flow', shape: 'Terminator'}
    },
    {
        id: 'Init', width: 140, height: 50, offsetX: 300, offsetY: 140,
        shape: { type: 'Flow', shape: 'Process' },
        annotations: [{ content: 'var i = 0;' }]
    }
];
let connectors: ConnectorModel = {
    // Unique name for the connector
    id: "connector1",
    // Source and Target node's name to which connector needs to be connected.
    sourceID: "Start",
    targetID: "Init",
    type: 'Orthogonal'
};

let diagram: Diagram = new Diagram({
    width: '100%', height: '600px', nodes: nodes, connectors: [connectors]
});

diagram.appendTo('#element');

```

{% endtab %}

Default values for all `nodes` and `connectors` can be set using the `getNodeDefaults` and `getConnectorDefaults` properties, respectively. For example, if all nodes have the same width and height, such properties can be moved into `getNodeDefaults`.

### Complete flow diagram

Similarly, the required nodes and connectors can be added to form a complete flow diagram.

{% tab template= "diagram/getting-started", es5Template="es5flow" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [
    { id: 'Start', offsetY: 50, annotations: [{ content: 'Start' }], shape: { type: 'Flow', shape: 'Terminator' } },
    { id: 'Init', offsetY: 140, annotations: [{ content: 'var i = 0;' }], shape: { type: 'Flow', shape: 'Process' } },
    { id: 'Condition', offsetY: 230, annotations: [{ content: 'i < 10?' }], shape: { type: 'Flow', shape: 'Decision' } },
    { id: 'Print', offsetY: 320, annotations: [{ content: 'print(\'Hello!!\');' }], shape: { type: 'Flow', shape: 'PreDefinedProcess' } },
    { id: 'Increment', offsetY: 410, annotations: [{ content: 'i++;' }], shape: { type: 'Flow', shape: 'Process' } },
    { id: 'End', offsetY: 500, annotations: [{ content: 'End' }], shape: { type: 'Flow', shape: 'Terminator' } },
];

let connector: ConnectorModel[] = [
    { id: 'connector1', sourceID: 'Start', targetID: 'Init' },
    { id: 'connector2', sourceID: 'Init', targetID: 'Condition' },
    { id: 'connector3', sourceID: 'Condition', targetID: 'Print', annotations: [{ content: 'Yes' }] },
    {
        id: 'connector4', sourceID: 'Condition', targetID: 'End', annotations: [{ content: 'No' }],
        type: 'Orthogonal',
        segments: [
            { type: 'Orthogonal', length: 30, direction: "Right" },
            { type: 'Orthogonal', length: 300, direction: "Bottom" }
        ]
    },
    { id: 'connector5', sourceID: 'Print', targetID: 'Increment' },
    {
        id: 'connector6', sourceID: 'Increment', targetID: 'Condition',
        type: 'Orthogonal',
        segments: [
            { type: 'Orthogonal', length: 30, direction: "Left" },
            { type: 'Orthogonal', length: 200, direction: "Top" }
        ]
    }];

let diagram: Diagram = new Diagram({
    width: '100%', height: '600px', nodes: nodes, connectors: connector,
    getNodeDefaults: (node: NodeModel) => {
        node.height = 50;
        node.width = 140;
        node.offsetX = 300;
        return node;
    },
    getConnectorDefaults: (obj: ConnectorModel): ConnectorModel => {
        obj.type = "Orthogonal";
        obj.targetDecorator = { shape: 'Arrow', width: 10, height: 10 };
        return obj;
    }
});

diagram.appendTo('#element');

```

{% endtab %}

## Automatic organization chart

In the 'Flow Diagram' section, how to create a diagram manually was discussed. This section explains how to create and position the diagram automatically.

### Business object (Employee information)

Define Employee Information as JSON data. The following code example shows an employee array whose, `Name` is used as an unique identifier and `ReportingPerson` is used to identify the person to whom an employee report to, in the organization.

```typescript

//Initialize data source...
let data: object[] = [{Name: "Elizabeth", Role: "Director" },
{ Name: "Christina", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Yoshi", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Philip", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Yang", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Roland", ReportingPerson: "Yang", Role: "Lead" },
{ Name: "Yvonne", ReportingPerson: "Yang", Role: "Lead" }
];

```

### Map data source

You can configure the above "Employee Information" with diagram, so that the nodes and connectors are automatically generated using the mapping properties. The following code example show how `dataSourceSettings` is used to map ID and parent with property name identifiers for employee information.

```typescript

//Initialize data source...

let data: object[] = [{Name: "Elizabeth", Role: "Director" },
{ Name: "Christina", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Yoshi", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Philip", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Yang", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Roland", ReportingPerson: "Yang", Role: "Lead" },
{ Name: "Yvonne", ReportingPerson: "Yang", Role: "Lead" }
];

let items: DataManager = new DataManager(data as JSON[], new Query().take(7));

//Initialize data source...
let diagram: Diagram = new Diagram({
    width: '100%', height: '600px',

//Configure data source for diagram

    dataSourceSettings: {
        id: 'Name', parentId: 'ReportingPerson', dataManager: items
    }
});

```

### Visualize employee

The following code examples indicate how to define the default appearance of nodes and connectors. The `setNodeTemplate` is used to update each node based on employee data.

{% tab template= "diagram/getting-started", es5Template="es5DataBinding" %}

```typescript

import {
    Diagram, ConnectorModel, Node, DataBinding, HierarchicalTree, TreeInfo, SnapConstraints,
} from '@syncfusion/ej2-diagrams';
Diagram.Inject(DataBinding, HierarchicalTree);

import { DataManager, Query } from '@syncfusion/ej2-data';

export interface EmployeeInfo {
  Name: string;
  Role: string;
}

//To represent the roles
let codes: object[]  = {
    Director: "rgb(0, 139,139)",
    Manager: "rgb(30, 30,113)",
    Lead: "rgb(0, 100,0)"
}

// Bind custom data with node
function getNodeTemplate(node) {
    node.annotations[0].content = (node.data as EmployeeInfo).Name;
    node.style.fill = codes[(node.data as EmployeeInfo).Role];
}

let data: object[] = [{Name: "Elizabeth", Role: "Director" },
{ Name: "Christina", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Yoshi", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Philip", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Yang", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Roland", ReportingPerson: "Yang", Role: "Lead" },
{ Name: "Yvonne", ReportingPerson: "Yang", Role: "Lead" }
];

let items: DataManager = new DataManager(data as JSON[], new Query().take(7));

let diagram: Diagram = new Diagram({
    width: '100%', height: '600px',
    snapSettings: { constraints: SnapConstraints.None },
    //Use automatic layout to arrange elements on the page
    layout: {
        type:'OrganizationalChart',
        margin: {left: 10, top: 10},
        horizontalSpacing: 50,
        verticalSpacing: 50,
        orientation:'TopToBottom',
        getLayoutInfo: (node: Node, tree: TreeInfo) => {
            if (!tree.hasSubTree) {
                tree.orientation = 'Vertical';
                tree.type = 'Alternate';
                }
        }
    },
    dataSourceSettings: {
        id: 'Name', parentId: 'ReportingPerson', dataManager: items
    },

    getNodeDefaults: (obj: Node, diagram: Diagram) => {
        obj.height = 30; obj.width = 70;
        obj.shape = {type: 'Basic', shape: 'Rectangle'};
        obj.annotations = [{
            id: "label1",
            style:{
            fontSize: 11,
            bold: true,
            fontFamily: "Segoe UI",
            color: "white"
            }
        }]
            return obj;
    },
    getConnectorDefaults: (connector: ConnectorModel, diagram: Diagram) => {
        connector.targetDecorator.shape = 'Arrow';
        connector.type = 'Orthogonal';
        return connector;
    },
    setNodeTemplate: (node: NodeModel) => {
        return getNodeTemplate(node);
        }
});

diagram.appendTo('#element');

```

{% endtab %}