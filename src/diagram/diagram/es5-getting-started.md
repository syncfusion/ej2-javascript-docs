---
title: "Getting Started"
component: "Diagram"
description: "Diagram getting started creates your first flow diagram and organizational chart diagram."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myApp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-diagrams/dist/global/ej2-diagrams.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-diagrams/styles/material.css`

**Step 3:** Create a folder `myApp/resources` and copy/paste the global scripts and styles from the above installed location to `myApp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myApp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Diagram's global script -->
            <script src="resources/ej2-diagrams.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Diagram` element and initiate the `Essential JS 2 Diagram` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Diagram's global script -->
            <script src="resources/ej2-diagrams.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="element">Diagram</div>
            <script>
                // initialize diagram component
                var diagram = new ej.diagrams.Diagram();

                // Render initialized diagram.
                diagram.appendTo('#element')
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Diagram** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myApp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-diagrams/dist/global/ej2-diagrams.min.js`](http://cdn.syncfusion.com/ej2/ej2-diagrams/dist/global/ej2-diagrams.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-diagrams/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-diagrams/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myApp` location and add the CDN link references. Now, add the `Diagram` element and initiate the `Essential JS 2 Diagram` component in the index.html by using following code.

{% tab template="diagram/getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-diagrams/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Diagram's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-diagrams/dist/global/ej2-diagrams.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element  -->
             <div id="element">Diagram</div>
            <script>
                // initialize diagram component
                var diagram = new ej.diagrams.Diagram();

                // Render initialized diagram.
                diagram.appendTo('#element')
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Diagram` component.

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

Add two node to the diagram as shown in the previous example. Connect these nodes by adding a connector using the `connector` property and refer the source and target end by using the `sourceNode` and `targetNode` properties.

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

```javascript

//Initialize data source...
var data = [{Name: "Elizabeth", Role: "Director" },
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

```javascript

//Initialize data source...

var data = [{Name: "Elizabeth", Role: "Director" },
{ Name: "Christina", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Yoshi", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Philip", ReportingPerson: "Christina", Role: "Lead" },
{ Name: "Yang", ReportingPerson: "Elizabeth", Role: "Manager" },
{ Name: "Roland", ReportingPerson: "Yang", Role: "Lead" },
{ Name: "Yvonne", ReportingPerson: "Yang", Role: "Lead" }
];

var items = new DataManager(data as JSON[], new Query().take(7));

//Initialize data source...
var diagram = new ej.diagrams.Diagram({
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