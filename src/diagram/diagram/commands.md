---
title: "Commands"
component: "Diagram"
description: "Diagram commands allow you to arrange or resize the selected objects or defined objects in the diagram area."
---

# Commands

<!-- markdownlint-disable MD010 -->

There are several commands available in the diagram as follows.

* Alignment commands
* Spacing commands
* Sizing commands
* Clipboard commands
* Grouping commands
* Z-order commands
* Zoom commands
* Nudge commands
* FitToPage commands
* Undo/Redo commands

## Align

Alignment commands enable you to align the selected or defined objects such as nodes and connectors with respect to the selection boundary. Refer to [`align`](../api/diagram#align) commands which shows how to use align methods in the diagram.

<!-- markdownlint-disable MD033 -->

| Parameters | Description |
|:------------| :------: |
|[`Alignment Options`](../api/diagram/alignmentOptions#AlignmentOptions) | <p align="left">Defines the specific direction, with respect to which the objects to be aligned. <br> The accepted values of the argument "alignment options" are as follows.</p> <table><tr><td> Left </td><td align="left"> Aligns all the selected objects at the left of the selection boundary. </td></tr><tr><td> Right </td><td align="left"> Aligns all the selected objects at the right of the selection boundary. </td></tr><tr><td> Center </td><td align="left"> Aligns all the selected objects at the center of the selection boundary. </td></tr><tr><td>Top </td><td align="left"> Aligns all the selected objects at the top of the selection boundary. </td></tr><tr><td> Bottom </td><td align="left"> Aligns all the selected objects at the bottom of the selection boundary. </td></tr><tr><td> Middle </td><td align="left"> Aligns all the selected objects at the middle of the selection boundary. </td></tr></table>|
| Objects | <p align="left">Defines the objects to be aligned. This is an optional parameter. By default, all the nodes and connectors in the selected region of the diagram gets aligned.</p> |
[`Alignment Mode`](../api/diagram/alignmentMode#AlignmentMode)  | <p align="left">Defines the specific mode, with respect to which the objects to be aligned. This is an optional parameter. The default alignment mode is `Object`.<br> The accepted values of the argument "alignment mode" are as follows.</p> <table><tr><td> Object </td><td align="left"> Aligns the objects based on the first object in the selected list. </td></tr><tr><td> Selector </td><td align="left"> Aligns the objects based on the selection boundary. </td></tr></table>|

The following code example illustrates how to align all the selected objects at the left side of the selection boundary.

```typescript
import {
    Diagram,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the node
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 100,
    height: 60,
    offsetX: 100,
    offsetY: 170,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node3: NodeModel = {
    id: 'node3',
    width: 140,
    height: 60,
    offsetX: 100,
    offsetY: 240,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};

//Initializes the Diagram Component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2, node3]
});
diagram.appendTo('#element');
let selArray: (NodeModel | ConnectorModel)[] = [];
selArray.push(diagram.nodes[0], diagram.nodes[1], diagram.nodes[2]);
//Selects the nodes
diagram.select(selArray);
//Sets direction as left
diagram.align('Left', diagram.selectedItems.nodes, 'Selector');
diagram.dataBind();
```

![Align Sample](images/Commands_img1.png)

## Distribute

The [`Distribute`](../api/diagram#distribute) commands enable to place the selected objects on the page at equal intervals from each other. The selected objects are equally spaced within the selection boundary.

The factor to distribute the shapes [`DistributeOptions`](../api/diagram/distributeOptions#DistributeOptions) are listed as follows:

* RightToLeft: Distributes the objects based on the distance between the right and left sides of the adjacent objects.
* Left: Distributes the objects based on the distance between the left sides of the adjacent objects.
* Right: Distributes the objects based on the distance between the right sides of the adjacent objects.
* Center: Distributes the objects based on the distance between the center of the adjacent objects.
* BottomToTop: Distributes the objects based on the distance between the bottom and top sides of the adjacent objects.
* Top: Distributes the objects based on the distance between the top sides of the adjacent objects.
* Bottom: Distributes the objects based on the distance between the bottom sides of the adjacent objects.
* Middle: Distributes the objects based on the distance between the vertical center of the adjacent objects.

The following code example illustrates how to execute the space commands.

```typescript
import {
    Diagram,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the node
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 240,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node3: NodeModel = {
    id: 'node3',
    width: 90,
    height: 60,
    offsetX: 170,
    offsetY: 150,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2, node3]
});
diagram.appendTo('#element');
let selArray: (NodeModel | ConnectorModel)[] = [];
selArray.push(diagram.nodes[0], diagram.nodes[1], diagram.nodes[2]);
//Selects the nodes
diagram.select(selArray);
//Distributes space between the nodes
diagram.distribute('RightToLeft', diagram.selectedItems.nodes);
```

![Distribute Sample](images/Commands_img2.png)

## Sizing

Sizing [`sameSize`](../api/diagram#sameSize) commands enable to equally size the selected nodes with respect to the first selected object.

[`SizingOptions`](../api/diagram/sizingOptions) are as follows:

* Width: Scales the width of the selected objects.
* Height: Scales the height of the selected objects.
* Size: Scales the selected objects both vertically and horizontally.

The following code example illustrates how to execute the size commands.

```typescript
import {
    Diagram,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the node
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 100,
    height: 60,
    offsetX: 100,
    offsetY: 170,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node3: NodeModel = {
    id: 'node3',
    width: 130,
    height: 60,
    offsetX: 100,
    offsetY: 230,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2, node3]
});
diagram.appendTo('#element');
let selArray: (NodeModel)[] = [];
selArray.push(diagram.nodes[0], diagram.nodes[1], diagram.nodes[2]);
//Selects the nodes
diagram.select(selArray);
//Resizes the selected nodes with the same width
diagram.sameSize('Width', diagram.selectedItems.nodes);
```

![Sizing Sample](images/Commands_img3.png)

## Clipboard

Clipboard commands are used to cut, copy, or paste the selected elements. Refer to the following link which shows how to use clipboard methods in the diagram.

* Cuts the selected elements from the diagram to the diagram’s clipboard, [`cut`](../api/diagram#cut).

* Copies the selected elements from the diagram to the diagram’s clipboard, [`copy`](../api/diagram#copy).

* Pastes the diagram’s clipboard data (nodes/connectors) into the diagram, [`paste`](../api/diagram#paste).

The following code illustrates how to execute the clipboard commands.

{% tab template="diagram/commands", es5Template="es5clipboard" %}

```typescript

import {
    Diagram,
    ConnectorModel,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the connector
let connector: ConnectorModel = {
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
};

//Initializes the nodes
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 240,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};

//Initializes the Diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2],
    connectors: [connector]
});
diagram.appendTo('#element');
diagram.select([diagram.nodes[0], diagram.nodes[1], diagram.connectors[0]]);
//copies the selected nodes
diagram.copy();
//pastes the copied objects
diagram.paste(diagram.copy() as(NodeModel | ConnectorModel)[]);
```

{% endtab %}

## Grouping

**Grouping commands** are used to group/ungroup the selected elements on the diagram. Refer to the following link which shows how to use grouping commands in the diagram.

[`Group`](../api/diagram#group) the selected nodes and connectors in the diagram.

[`Ungroup`](../api/diagram#ungroup) the selected nodes and connectors in the diagram.

The following code illustrates how to execute the grouping commands.

{% tab template="diagram/commands", es5Template="es5grouping" %}

```typescript

import {
    Diagram,
    ConnectorModel,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the nodes
let nodes: NodeModel[] = [{
        id: 'node1',
        width: 100,
        height: 70,
        offsetX: 100,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node2',
        width: 100,
        height: 70,
        offsetX: 300,
        offsetY: 100,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'node3',
        width: 100,
        height: 70,
        offsetX: 200,
        offsetY: 200,
        style: {
            fill:   '#6BA5D7',
            strokeColor: 'white',
            strokeWidth: 1
        },
    },
    {
        id: 'group',
        children: ['node1', 'node2', 'connector1']
    },
    {
        id: 'group2',
        children: ['node3', 'group']
    }
];

//Initializes the connector
let connector: ConnectorModel = {
    id: 'connector1',
    sourceID: 'node1',
    targetID: 'node2',
    style: {
        strokeColor : '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth :  2,
        targetDecorator: {
            style: {
                fill : '#6BA5D7',
                strokeColor :   '#6BA5D7'
            }
        }
    }
};

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: nodes,
    connectors: [connector],
});
diagram.appendTo('#element');
//Selects the diagram
diagram.selectAll();
//Groups the selected elements.
diagram.group();
```

{% endtab %}

## Z-Order command

**Z-Order commands** enable you to visually arrange the selected objects such as nodes and connectors on the page.

### bringToFront command

The [`bringToFront`](../api/diagram#bringToFront) command visually brings the selected element to front over all the other overlapped elements. The following code illustrates how to execute the `bringToFront` command.

{% tab template="diagram/commands", es5Template="es5bringfront" %}

```typescript
import {
    Diagram,
    ConnectorModel,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the nodes
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 240,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node3: NodeModel = {
    id: 'node3',
    width: 90,
    height: 60,
    offsetX: 160,
    offsetY: 90,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2, node3]
});
let selArray: (NodeModel)[] = [];
diagram.appendTo('#element');
selArray.push(diagram.nodes[2]);
//Selects the nodes
diagram.select(selArray);
//Brings to front
diagram.bringToFront();

```

{% endtab %}

### sendToBack command

The [`sendToBack`](../api/diagram#sendToBack) command visually moves the selected element behind all the other overlapped elements. The following code illustrates how to execute the `sendToBack` command.

{% tab template="diagram/commands", es5Template="es5sendback" %}

```typescript
import {
    Diagram,
    NodeModel
} from '@syncfusion/ej2-diagrams';

//Initializes the nodes
let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 240,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node3: NodeModel = {
    id: 'node3',
    width: 90,
    height: 60,
    offsetX: 160,
    offsetY: 90,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2, node3]
});
let selArray: (NodeModel)[] = [];
diagram.appendTo('#element');
selArray.push(diagram.nodes[2]);
//Selects the nodes
diagram.select(selArray);
//Sends to back
diagram.sendToBack();
```

{% endtab %}

### moveForward command

The [`moveForward`](../api/diagram#moveForward) command visually moves the selected element over the nearest overlapping element. The following code illustrates how to execute the `moveForward` command.

{% tab template="diagram/commands", es5Template="es5moveforward" %}

```typescript
import {
    Diagram,
    NodeModel
} from '@syncfusion/ej2-diagrams';

let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 180,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2]
});
let selArray: (NodeModel)[] = [];
diagram.appendTo('#element');
selArray.push(diagram.nodes[1]);
//Selects the nodes
diagram.select(selArray);
//Moves forward
diagram.moveForward();
```

{% endtab %}

### sendBackward command

The [`sendBackward`](../api/diagram#sendBackward) command visually moves the selected element behind the underlying element. The following code illustrates how to execute the `sendBackward` command.

{% tab template="diagram/commands", es5Template="es5sendbackward" %}

```typescript
import {
    Diagram,
    ConnectorModel,
    NodeModel
} from '@syncfusion/ej2-diagrams';

let node: NodeModel = {
    id: 'node1',
    width: 90,
    height: 60,
    offsetX: 100,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
let node2: NodeModel = {
    id: 'node2',
    width: 90,
    height: 60,
    offsetX: 180,
    offsetY: 100,
    style: {
        fill:   '#6BA5D7',
        strokeColor: 'white',
        strokeWidth: 1
    },
};
//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    nodes: [node, node2]
});
let selArray: (NodeModel)[] = [];
diagram.appendTo('#element');
selArray.push(diagram.nodes[1]);
diagram.select(selArray);
//Sends backward
diagram.sendBackward();
```

{% endtab %}

## Zoom

The [`zoom`](../api/diagram#zoom) command is used to zoom-in and zoom-out the diagram view.

The following code illustrates how to zoom-in/zoom out the diagram.

```typescript
import {
    Diagram
} from '@syncfusion/ej2-diagrams';

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
});
diagram.appendTo('#element');
// Sets the zoomFactor
//Defines the focusPoint to zoom the diagram with respect to any point
//When you do not set focus point, zooming is performed with reference to the center of current diagram view.
diagram.zoom(1.2, {
    x: 100,
    y: 100
});

```

## Nudge command

The [`nudge`](../api/diagram#nudge) commands move the selected elements towards up, down, left, or right by 1 pixel.

[`NudgeDirection`](../api/diagram/nudgeDirection) nudge command moves the selected elements towards the specified direction by 1 pixel, by default.

The accepted values of the argument "direction" are as follows:

* Up: Moves the selected elements towards up by the specified delta value.
* Down: Moves the selected elements towards down by the specified delta value.
* Left: Moves the selected elements towards left by the specified delta value.
* Right: Moves the selected elements towards right by the specified delta value.

The following code illustrates how to execute nudge command.

```typescript
import {
    Diagram
} from '@syncfusion/ej2-diagrams';

//Initializes the Diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
});
diagram.appendTo('#element');
//Nudges to right
diagram.nudge('Right');

```

## Nudge by using arrow keys

The corresponding arrow keys are used to move the selected elements towards up, down, left, or right direction by 1 pixel.

![Nudge Command](images/Commands_img4.png)

Nudge commands are particularly useful for accurate placement of elements.

## BringIntoView

The [`bringIntoView`](../api/diagram#bringIntoView) command brings the specified rectangular region into the viewport of the diagram.

The following code illustrates how to execute the `bringIntoView` command.

```typescript
import {
    Diagram,
    Rect
} from '@syncfusion/ej2-diagrams';

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
});
diagram.appendTo('#element');
//Brings the specified rectangular region of the diagram content to the viewport of the page.
let bound: Rect = new Rect(200, 400, 500, 400);
diagram.bringIntoView(bound);

```

## BringToCenter

The [`bringToCenter`](../api/diagram#bringToCenter) command brings the specified rectangular region of the diagram content to the center of the viewport.

The following code illustrates how to execute the `bringToCenter` command.

```typescript
import {
    Diagram,
    Rect
} from '@syncfusion/ej2-diagrams';

//Initializes the Diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
});
diagram.appendTo('#element');
//Brings the specified rectangular region of the Diagram content to the center of the viewport.
let bound: Rect = new Rect(200, 400, 500, 400);
diagram.bringToCenter(bound);

```

## FitToPage command

The [`fitToPage`](../api/diagram#fitToPage) command helps to fit the diagram content into the view with respect to either width, height, or at the whole.

The [`mode`](../api/diagram/fitModes#modes) parameter defines whether the diagram has to be horizontally/vertically fit into the viewport with respect to width, height, or entire bounds of the diagram.

The [`region`](../api/diagram/diagramRegions#region) parameter defines the region that has to be drawn as an image.

The [`margin`](../api/diagram/iFitOptions#margin) parameter defines the region/bounds of the diagram content that is to be fit into the view.

The [`canZoomIn`](../api/diagram/iFitOptions#canZoomIn) parameter enables/disables zooming to fit the smaller content into a larger viewport.

The [`customBounds`](../api/diagram/iFitOptions#customBounds) parameter the custom region that has to be fit into the viewport.

The following code illustrates how to execute `FitToPage` command.

```typescript
import {
    Diagram
} from '@syncfusion/ej2-diagrams';

//Initializes the Diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
});
diagram.appendTo('#element');
//fit the diagram to the page with respect to mode and region
diagram.fitToPage({
    mode: 'Page',
    region: 'Content',
    margin: {
        bottom: 50
    },
    canZoomIn: false
});

```

## Command manager

Diagram provides support to map/bind command execution with desired combination of key gestures. Diagram provides some built-in commands.
[`CommandManager`](../api/diagram/commandManager#commandManager) provides support to define custom commands. The custom commands are executed, when the specified key gesture is recognized.

## Custom command

To define a custom command, specify the following properties:
* [`execute`](../api/diagram/command#execute): A method to be executed.
* [`canExecute`](../api/diagram/command#canexecute): A method to define whether the command can be executed at the moment.
* [`gesture`](../api/diagram/keyGestureModel#gesture): A combination of [`keys`](../api/diagram/keys#key) and [`KeyModifiers`](../api/diagram/keyModifiers#keymodifiers).
* [`parameter`](../api/diagram/command#parameter): Defines any additional parameters that are required at runtime.
* [`name`](../api/diagram/command#name): Defines the name of the command.

To explore the properties of custom commands, refer to [`Commands`](../api/diagram/command#commands).

The following code example illustrates how to define a custom command.

```typescript
import {
    Diagram,
    Keys,
    KeyModifiers
} from '@syncfusion/ej2-diagrams';

//Initializes the Diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            //Method to define whether the command can be executed at the current moment
            canExecute: function() {
                //Defines that the clone command can be executed, if and only if the selection list is not empty.
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            //Command handler
            execute: function() {
                //Logic to clone the selected element
                diagram.copy();
                diagram.paste();
                diagram.dataBind();
            },
            //Defines that the clone command has to be executed on the recognition of key press.
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift | KeyModifiers.Alt
            }
        }]
    },
});
diagram.appendTo('#element');
```

## Modify the existing command

When any one of the default commands is not desired, they can be disabled. To change the functionality of a specific command, the command can be completely modified.

The following code example illustrates how to disable a command and how to modify the built-in commands.

```typescript
import {
    Diagram,
    Keys,
    KeyModifiers
} from '@syncfusion/ej2-diagrams';

//Initializes the diagram component
let diagram: Diagram = new Diagram({
    width: '100%',
    height: '350px',
    //Disables the nudging commands
    commandManager: {
        commands: {
            //Assigns null value to an existing command and disables its execution
            "nudgeUp": null,
            "nudgeDown": null,
            "nudgeRight": null,

            //Modifies the existing command - nudgeLeft
            "nudgeLeft": {
                canExecute: function(args)
                if (args.model.selectedItems.length) {
                    return true;
                }
            },

            //Command handler
            execute: function(args) {
                diagram.nudge("left");
            },

            gesture: {
                key: Keys.Left
            }
        }
    }
}
});
diagram.appendTo('#element');

```

## See Also

* [How to create the custom context menu items](../context-menu)