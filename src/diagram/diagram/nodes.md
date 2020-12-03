---
title: "Node"
component: "Diagram"
description: "Nodes visually represents the geometrical information and process flows."
---

# Node

Nodes are graphical objects used to visually represent the geometrical information, process flow, internal business procedure, entity, or any other kind of data.

![Node](images/node.png)

<!-- markdownlint-disable MD033 -->

## Create node

A node can be created and added to the diagram, either programmatically or interactively. Nodes are stacked on the diagram area from bottom to top in the order they are added.

## Add node through nodes collection

To create a node, define the [`node`](../api/diagram/node) object and add that to nodes collection of the diagram model. The following code example illustrates how to add a node to the diagram.

{% tab template= "diagram/nodes", es5Template="es5Node" %}

```typescript

import { Diagram, NodeModel } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.

let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        fill: '#6BA5D7',
        strokeColor: 'white'
    },
    // Text(label) added to the node
};

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized Diagram
diagram.appendTo('#element');

```

{% endtab %}

>Note: Node id should not begin with numbers(should begin with a letter).Node Id should be unique for all the shapes and connectors.

## Add/Remove node at runtime

* Nodes can be added at runtime by using public method, add and can be removed at runtime by using public method,
remove. On adding node at runtime, the nodes collection is changed and the [`collectionChange`](../api/diagram#collectionChange--emittypecollectionchangeeventargs) event will trigger.

* The node’s ID property is used to define the name of the node and its further used to find the node at runtime and do any customization.

The following code illustrates how to add a node.

{% tab template= "diagram/nodes", es5Template="es5run" %}

```typescript

import { Diagram, NodeModel } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        fill: '#6BA5D7',
        strokeColor: 'white'
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px'
});
// render initialized diagram
diagram.appendTo('#element');

//Add Node
diagram.add(node);
```

{% endtab %}

## Add node from palette

Nodes can be predefined and added to the palette, and can be dropped into the diagram when needed. For more information
about adding nodes from symbol palette, refer to [`Symbol Palette`](../api/diagram/symbolPaletteModel).

* Once you drag a node/connector from the palette to the diagram, the following events can be used to do your customization.
* When a symbol is dragged into diagram from symbol palette, the [`dragEnter`](../api/diagram#dragEnter--emittypeidragentereventargs>) event gets triggered.
* When a symbol is dragged over diagram, the [`dragOver`](../api/diagram#dragOver--emittypeidragovereventargs>) event gets triggered.
* When a symbol is dragged and dropped from symbol palette to diagram area, the [`drop`](../api/diagram#drop--emittypeidropeventargs>) event gets triggered.
* When a symbol is dragged outside of the diagram, the [`dragLeave`](../api/diagram#dragLeave--emittypeidragleaveeventargs>) event gets triggered.

## Create node through data source

Nodes can be generated automatically with the information provided through data source. The default properties for
these nodes are fetched from default settings. For more information about data source, refer to Data Binding.

## Draw nodes

Nodes can be interactively drawn by clicking and dragging the diagram surface by using `NodeDrawingTool`. For more
information about drawing nodes, refer to Draw Nodes.

## Position

* Position of a node is controlled by using its [`offsetX`](../api/diagram/node#offsetX-number) and [`offsetY`](../api/diagram/node#offsetY-number) properties. By default, these offset properties represent the distance between the origin of the diagram’s page and node’s center point.

* You may expect this offset values to represent the distance between page origin and node’s top-left corner instead of center. The Pivot property helps to solve this problem. Default value of node’s [`pivot`](../api/diagram/node#pivot--pointmodel) point is (0.5, 0.5), that means center of the node.

* The size of the node can be controlled by using its [`width`](../api/diagram/node#width-number) and
[`height`](../api/diagram/node#height-number) properties.

* Rotation of a node is controlled by using its [`rotateAngle`](../api/diagram/node#rotateAngle-number) property.

The following table illustrates how pivot relates offset values with node boundaries.

| Pivot | Offset |
|-------- | -------- |
| (0.5,0.5)| offsetX and offsetY values are considered as the node’s center point. |
| (0,0) | offsetX and offsetY values are considered as the top-left corner of the node. |
| (1,1) | offsetX and offsetY values are considered as the bottom-right corner of the node. |

The following code illustrates how to change the `pivot` value.

{% tab template= "diagram/nodes", es5Template="es5position" %}

```typescript

import { Diagram, NodeModel } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    pivot: {
        x: 0,
        y: 0
    }
    style: {
        fill: '#6BA5D7',
        strokeColor: 'white'
    },
    // Text(label) added to the node
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');
diagram.select([diagram.nodes[0]]);
```

{% endtab %}

## Flip

The diagram Provides support to flip the node. [`flip`](../api/diagram/node#flip) is performed to
give the mirrored image of the original element.

The flip types are as follows:

* HorizontalFlip
 [`Horizontal`](../api/diagram/flipDirection) is used to change the element in horizontal direction.

* VerticalFlip
[`Vertical`](../api/diagram/flipDirection) is used to change the element in vertical direction

* Both
[`Both`](../api/diagram/flipDirection) which involves both vertical and horizontal changes of the element.

The following code illustrates how to provide the mirror image of the original element.

{% tab template= "diagram/nodes", es5Template="es5NodeFlip" %}

```typescript

import { Diagram, NodeModel ,BasicShapeModel} from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    // Flip the node in Horizontal Direction
    flip:"Horizontal",
      shape: {
        type: 'Basic',
        shape: 'RightTriangle',
    },
    style: {
        fill: '#6BA5D7',
        strokeDashArray: '5,5'
    },
};

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized Diagram
diagram.appendTo('#element');

```

{% endtab %}

## Appearance

* The appearance of a node can be customized by changing its [`fill`](../api/diagram/shapeStyleModel#fill-string) color, [`borderColor`](../api/diagram/node#borderColor-string), [`borderWidth`](../api/diagram/node#borderWidth-number), [`strokeDashArray`](../api/diagram/shapeStyleModel#strokeDashArray-number),
[`opacity`](../api/diagram/shapeStyleModel#opacity-number), and [`shadow`](../api/diagram/shapeStyleModel#shadow-number).

* The [`visible`](../api/diagram/node#visible-boolean) property of the node enables or disables the visibility of the node.

The following code illustrates how to customize the appearance of the shape.

{% tab template= "diagram/nodes", es5Template="es5Appear" %}

```typescript

import { Diagram, NodeModel } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        fill: '#6BA5D7',
        strokeDashArray: '5,5'
    },
    borderWidth: 2,
    borderColor: 'red',
    // Text(label) added to the node
};

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized Diagram
diagram.appendTo('#element');

```

{% endtab %}

>Note: The flip is also applicable for group and BPMN shapes.

## Gradient

The [`gradient`](../api/diagram/shapeStyleModel#gradient-gradientmodel) property of the node allows you to define and apply the gradient effect to that node.

The gradient stop property defines the color and a position, where the previous color transition ends and a new color transition starts.

The gradient stop’s opacity property defines the transparency level of the region.

There are two types of gradients as follows:

* Linear gradient

* Radial gradient

## Linear gradient

* [`LinearGradient`](../api/diagram/shapeStyleModel#linearGradient-lineargradientmodel) defines a smooth transition between a set of colors (so-called stops) on a line.

* A linear gradient’s x1, y1, x2, y2 properties are used to define the position (relative to the node) of the rectangular region that needs to be painted.

{% tab template= "diagram/nodes", es5Template="es5Gradient" %}

```typescript

import { Diagram, NodeModel, NodeConstraints } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let linearGradient: GradientModel | LinearGradientModel | RadialGradientModel;
linearGradient = {
    //Start point of linear gradient
    x1: 0,
    y1: 0,
    //End point of linear gradient
    x2: 50,
    y2: 50,
    //Sets an array of stop objects
    stops: [{
            color: 'white',
            offset: 0
        },
        {
            color: '#6BA5D7',
            offset: 100
        }
    ],
    type: 'Linear'
};
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        gradient: linearGradient
    }
    // Text(label) added to the node
};


// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Radial gradient

* [`RadialGradient`](../api/diagram/shapeStyleModel#radialGradient-radialgradientmodel) defines a smooth transition between stops on a circle.

* A radial gradient’s cx, cy, fx, fy properties are used to define the position (relative to the node) of the outermost or the innermost circle of the radial gradient.

{% tab template= "diagram/nodes", es5Template="es5Gradient" %}

```typescript

import { Diagram, NodeModel, NodeConstraints } from '@syncfusion/ej2-diagrams';

let radialGradient: GradientModel | LinearGradientModel | RadialGradientModel;
radialGradient = {
    //Center point of outer circle
    cx: 50,
    cy: 50,
    //Center point of inner circle
    fx: 25,
    fy: 25,
    //Radius of a radial gradient
    r: 50,
    //Sets an array of stop objects
    stops: [{
            color: 'white',
            offset: 0
        },
        {
            color: '#6BA5D7',
            offset: 100
        }
    ],
    type: 'Radial'
};
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        gradient: radialGradient
    }
    // Text(label) added to the node
};



// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Shadow

Diagram provides support to add [`shadow`](../api/diagram/node#shadow-shadowmodel) effect to a node that is disabled, by default. It can be enabled with the
constraints property of the node. The following code illustrates how to drop shadow.

{% tab template= "diagram/nodes", es5Template="es5shadow" %}

```typescript

import { Diagram, NodeModel, NodeConstraints } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.

let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        fill: '#6BA5D7',
        strokeColor: 'white'
    },
    constraints: NodeConstraints.Default | NodeConstraints.Shadow,
    // Text(label) added to the node
};

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized Diagram
diagram.appendTo('#element');
```

{% endtab %}

## Customizing shadow

The angle, distance, and opacity of the shadow can be customized with the shadow property of the node. The following code
example illustrates how to customize shadow.

{% tab template= "diagram/nodes", es5Template="es5shadow2" %}

```typescript

import { Diagram, NodeModel, NodeConstraints } from '@syncfusion/ej2-diagrams';

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    style: {
        fill: '#6BA5D7',
        strokeColor: 'white'
    },
    constraints: NodeConstraints.Default | NodeConstraints.Shadow,
    shadow: {
        angle: 50,
        opacity: 0.8,
        distance: 9
    }
    // Text(label) added to the node
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');
```

{% endtab %}

## Icon

Diagram provides support to describe the state of the node. i.e., the node is expanded or collapsed state.

>Note: Icon can be created only when the node has outEdges.

* To explore the properties of expand and collapse icon, refer to [`expandIcon`](../api/diagram/node#expandIcon-iconshapemodel) and [`collapseIcon`](../api/diagram/node#collapseIcon-iconshapemodel).

* The expandIcon’s and collapseIcon’s shape properties allow to define the shape of the icon.

The following code example illustrates how to create an icon of various shapes.

{% tab template= "diagram/nodes", es5Template="es5Icon" %}

```typescript

import { Diagram, NodeModel, ConnectorModel } from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: 'Start',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 50,
        annotations: [{
            content: 'Node1'
        }],
        style: {
            fill: '#6BA5D7',
            strokeColor: 'white'
        },
        expandIcon: {
            shape: 'ArrowDown',
            width: 10,
            height: 10
        },
        collapseIcon: {
            shape: 'ArrowUp',
            width: 10,
            height: 10
        }
    },
    {
        id: 'Init',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 140,
        style: {
            fill: '#6BA5D7',
            strokeColor: 'white'
        },
        annotations: [{
            content: 'Node2'
        }],
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
    width: '100%',
    height: '600px',
    nodes: nodes,
    connectors: [connectors]
});

diagram.appendTo('#element');

```

{% endtab %}

## Customizing expand icon

* Set the borderColor, borderWidth, and background color for an expandIcon using borderColor, borderWidth, and fill properties.

* Set a size for an expandIcon by using width and height properties.

* The expand icon can be aligned relative to the node boundaries. It has margin, offset, horizontalAlignment, and verticalAlignment settings. It is quite tricky, when all four alignments are used together but gives you more control over alignment.

## Customizing collapse icon

* Set the [`borderColor`](../api/diagram/iconShapeModel#borderColor-string),
[`borderWidth`](../api/diagram/iconShapeModel#borderWidth-number), background color for an collapseIcon using borderColor, borderWidth, and [`fill`](../api/diagram/iconShapeModel#fill-string) properties.

* Set a size for collapseIcon by using [`width`](../api/diagram/iconShapeModel#width-number) and
[`height`](../api/diagram/iconShapeModel#height-number) properties.

* Like expand icon, collapse icon also can be aligned relative to the node boundaries. It has margin, offset, horizontalAlignment, and verticalAlignment settings. It is quite tricky, when all four alignments are used together but gives you more control over alignment.

## Interaction

Diagram provides support to drag, resize, or rotate the node interactively. For more information about editing a node at runtime, refer to Edit Nodes.

## Constraints

The constraints property of the node allows you to enable/disable certain features. For more information about node constraints, refer to [`Node Constraints`](../api/diagram/node#constraints-nodeconstraints).

## Custom properties

The [`addInfo`](../api/diagram#addInfo-object) property of the node allows to maintain additional information to the node.

## Stack order

The nodes z-order property specifies the stack order of the node. A node with greater stack order is always in front of a node with a lower stack order.

## Data flow

Node has the InEdges and OutEdges read-only property. In this property, you can find what are all the connectors that are connected to the node, and then you can find these connectors by using the [`getObject`](../api/diagram#getObject) method in the diagram.

```typescript

let node: NodeModel = {
    id: 'node1',
    // Position of the node
    offsetX: 450,
    offsetY: 100,
    // Size of the node
    width: 80,
    height: 50,
    style: { fill: '#6BA5D7', strokeColor: 'white' },
};
let node2: NodeModel = {
    id: 'node2',
    // Position of the node
    offsetX: 350,
    offsetY: 200,
    // Size of the node
    width: 80,
    height: 50,
    style: { fill: '#6BA5D7', strokeColor: 'white' },
};
let node3: NodeModel = {
    id: 'node3',
    // Position of the node
    offsetX: 450,
    offsetY: 200,
    // Size of the node
    width: 80,
    height: 50,
    style: { fill: '#6BA5D7', strokeColor: 'white' },
};
let node4: NodeModel = {
    id: 'node4',
    // Position of the node
    offsetX: 550,
    offsetY: 200,
    // Size of the node
    width: 80,
    height: 50,
    style: { fill: '#6BA5D7', strokeColor: 'white' },
};
let connector: ConnectorModel = {
    id: 'connector1', sourceID: 'node1', targetID: 'node2', type: 'Orthogonal'
};
let connector2: ConnectorModel = {
    id: 'connector2', sourceID: 'node1', targetID: 'node3', type: 'Orthogonal'
};
let connector3: ConnectorModel = {
    id: 'connector3', sourceID: 'node1', targetID: 'node4', type: 'Orthogonal'
};

let diagram: Diagram = new Diagram({
    width: '100%', height: 600, nodes: [node, node2, node3, node4],
    connectors: [connector, connector2, connector3]
});
diagram.appendTo('#element');
diagram.getObject('connector1');
```

## See Also

* [How to add annotations to the node](./labels)
* [How to add ports to the node](./ports)
* [How to enable/disable the behavior of the node](./constraints)
* [How to add nodes to the symbol palette](./symbol-palette)
* [How to edit the node visual interface](./interaction#selection)
* [How to create diagram nodes using drawing tools](./tools)
