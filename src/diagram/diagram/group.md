---
title: "Group"
component: "Diagram"
description: "Diagram supports Grouping feature to group two or more nodes."
---

# Group

Group is used to cluster multiple nodes and connectors into a single element. It acts like a container for its children (nodes, groups, and connectors). Every change made to the group also affects the children. Child elements can be edited individually.

## Create group

## Add group when initializing diagram

A group can be added to the diagram model through [`nodes`](../api/diagram#nodes-NodeModel) collection. To define an object as group, add the child objects to the [`children`](../api/diagram/node#children-string) collection of the group. The following code illustrates how to create a group node.

* While creating group, its child node need to be declared before the group declaration.

* Add a node to the existing group child by using the `diagram.group` method.

* The group’s `diagram.unGroup` method is used to define whether the group can be ungrouped or not.

* A group can be added into a child of another group.

{% tab template= "diagram/group", es5Template="es5group" %}

```typescript

import {Diagram,NodeModel,} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: "rectangle1",
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'rectangle1'
        }]
    }, {
        id: "rectangle2",
        offsetX: 200,
        offsetY: 200,
        width: 100,
        height: 100,
        annotations: [{
            content: 'rectangle2'
        }]
    },
     {
            id: "rectangle3",
            offsetX: 400,
            offsetY: 300,
            width: 100,
            height: 100,
            style: { fill: 'darkCyan', strokeWidth: 2 },
            annotations: [{ content: 'rectangle2' }]
        }
    // Grouping node 1 and node 2 into a single group
    {
        id: 'group',
        children: ['rectangle1', 'rectangle2']
    },

];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');
diagram.selectAll();
// Adding the third node into the existing group
diagram.group();

```

{% endtab %}

The following code illustrates how a ungroup  at runtime.

{% tab template= "diagram/group", es5Template="es5ungroup" %}

```typescript

import {Diagram,NodeModel,} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: "rectangle1",
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'rectangle1'
        }]
    }, {
        id: "rectangle2",
        offsetX: 200,
        offsetY: 200,
        width: 100,
        height: 100,
        annotations: [{
            content: 'rectangle2'
        }]
    },
    {
        id: 'group',
        children: ['rectangle1', 'rectangle2']
    },

];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');
diagram.selectAll();
// Ungroup the selected group into nodes
diagram.unGroup();

```

{% endtab %}

## Add group at runtime

A group node can be added at runtime by using the client-side method `diagram.add`.

The following code illustrates how a group node is added at runtime.

{% tab template= "diagram/group", es5Template="es5groupadd" %}

```typescript

import {Diagram,NodeModel,} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
    id: "rectangle1",
    offsetX: 100,
    offsetY: 100,
    width: 100,
    height: 100,
    annotations: [{
        content: 'rectangle1'
    }]
}, {
    id: "rectangle2",
    offsetX: 200,
    offsetY: 200,
    width: 100,
    height: 100,
    annotations: [{
        content: 'rectangle2'
    }]
}, ];
let group: NodeModel = {
    id: 'group2',
    children: ['rectangle1', 'rectangle2']
};
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
    nodes: nodes,
});
diagram.appendTo('#element');
// Add the group into the diagram
diagram.add(group);

```

{% endtab %}

## Container

Containers are used to automatically measure and arrange the size and position of the child elements in a predefined manner.
There are two types of containers available.

***Canvas***

* The canvas panel supports absolute positioning and provides the least layout functionality to its contained diagram elements.

* Canvas allows you to position its contained elements by using the margin and alignment properties.

* Rendering alone possible in canvas container.

* It allows elements to be either vertically or horizontally aligned.

* Child can be defined with the collection [`canvas.children`](../api/diagram/canvas#children-DiagramElement) property.

* Basic element can be defined with the collection of [`basicElements`](../api/diagram#basicElements-DiagramElement).

The following code illustrates how to add canvas panel.

{% tab template= "diagram/group", es5Template="es5canvas" %}

```typescript

import {Diagram,DiagramElement,Canvas} from '@syncfusion/ej2-diagrams';

let diagram: Diagram;
let canvas: Canvas;
let child1: DiagramElement;
let child2: DiagramElement;
canvas = new Canvas();
canvas.pivot = {
    x: 0,
    y: 0
};
canvas.offsetX = 75;
canvas.offsetY = 75;
canvas.style.fill = '#6BA5D7';

child1 = new DiagramElement();
child1.width = 100;
child1.height = 100;
child1.margin.left = child1.margin.top = 10;

child2 = new DiagramElement();
child2.width = 100;
child2.height = 100;
child2.margin.left = 190;
child2.margin.top = 190;

canvas.children = [child1, child2];

diagram = new Diagram({
    mode: 'SVG',
    width: '100%',
    height: '600px',
    // Defines the basic elements
    basicElements: [canvas]
});
diagram.appendTo('#element');

```

{% endtab %}

***Stack***

* Stack panel is used to arrange its children in a single line or stack order, either vertically or horizontally.

* It controls spacing by setting margin properties of child and padding properties of group. By default, a stack panel’s [`orientation`](../api/diagram/stackPanel#orientation-Orientation) is vertical.

The following code illustrates how to add a stack panel.

{% tab template= "diagram/group", es5Template="es5stack" %}

```typescript

import {Diagram,NodeModel,StackPanel,TextElement,} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
    id: 'node5',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7'
    },
    annotations: [{
        content: 'Custom Template',
        offset: {
            y: 1
        },
        verticalAlignment: 'Top'
    }]
}, ];

let getTextElement: Function = (text: string) => {
    let textElement: TextElement = new TextElement();
    textElement.width = 50;
    textElement.height = 20;
    textElement.content = text;
    return textElement;
};

let addRows: Function = (column: StackPanel) => {
    column.children.push(getTextElement('Row1'));
    column.children.push(getTextElement('Row2'));
    column.children.push(getTextElement('Row3'));
    column.children.push(getTextElement('Row4'));
};

let diagram: Diagram = new Diagram({
    width: '100%',
    height: 900,
    nodes: nodes,
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
    setNodeTemplate: (obj: NodeModel, diagram: Diagram): StackPanel => {
        if (obj.id.indexOf('node5') !== -1) {
            // It will be replaced with grid panel
            let table: StackPanel = new StackPanel();
            table.orientation = 'Horizontal';
            table.padding.left

            let column1: StackPanel = new StackPanel();
            column1.children = [];
            column1.children.push(getTextElement('Column1'));
            addRows(column1);

            let column2: StackPanel = new StackPanel();
            column2.children = [];
            column2.children.push(getTextElement('Column2'));
            addRows(column2);

            table.children = [column1, column2];
            return table;
        }
        return null;
    },
});
diagram.appendTo('#element');

```

{% endtab %}

## Difference between a basic group and containers

| Group | Container |
| -------- | -------- |
| It arranges the child elements based on the child elements position and size properties. | Each container has a predefined behavior to measure and arrange its child elements. Canvas and stack containers are supported in the diagram. |
| The Padding, Min, and Max Size properties are not applicable for basic group. | It is applicable for container. |
| The Children’s margin and alignment properties are not applicable for basic group. |  It is applicable for container. |

## Interaction

You can edit the group and its children at runtime. For more information about how to interact with a group, refer to `Edit Groups`.

## See Also

* [How to add annotations to the node](./labels)
* [How to add ports to the node](./ports)
* [How to enable/disable the behavior of the node](./constraints)
* [How to add nodes to the symbol palette](./symbol-palette)
* [How to create diagram nodes using drawing tools](./tools)
* [How to perform the interaction on the group](./interaction#selection)