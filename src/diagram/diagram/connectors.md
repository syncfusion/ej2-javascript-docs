---
title: "Connector"
component: "Diagram"
description: "Diagram connector allows you to draw a line to connect two points, nodes or ports."
---

# Connector

Connectors are objects used to create link between two points, nodes or ports to represent the relationships between them.

## Create connector

Connector can be created by defining the source and target point of the connector. The path to be drawn can be defined with a collection of segments. To explore the properties of a [`connector`](../api/diagram/connector), refer to [`Connector Properties`](../api/diagram/connector).

## Add connectors through connectors collection

The [`sourcePoint`](../api/diagram/connector#sourcepoint-PointModel) and [`targetPoint`](../api/diagram/connector#targetpoint-PointModel) properties of connector allow you to define the end points of a connector.

The following code example illustrates how to add a connector through connector collection.

{% tab template= "diagram/connectors", es5Template="es5Connectors" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';
let connectors: ConnectorModel = [{
    // Name of the connector
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Sets source and target points
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

## Add connector at runtime

Connectors can be added at runtime by using public method, `diagram.add` and can be removed at runtime by using public method, `diagram.remove`.

The following code example illustrates how to add connector at runtime.

{% tab template= "diagram/connectors", es5Template="es5Connectorsatruntime" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = {
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',

});

diagram.appendTo('#element');
// Adds to the diagram
diagram.add(connectors)
// Remove from the diagram
diagram.remove(connectors)

```

{% endtab %}

## Connectors from palette

Connectors can be predefined and added to the symbol palette. You can drop those connectors into the diagram, when required.

For more information about adding connectors from symbol palette, refer to `Symbol Palette`.

## Draw connectors

Connectors can be interactively drawn by clicking and dragging on the diagram surface by using `drawingObject`.

For more information about drawing connectors, refer to [`Draw Connectors`](../api/diagram#drawingObject-ConnectorModel).

## Update connector at runtime

Various connector properties such as `sourcePoint`, `targetPoint`, `style`, `sourcePortID`, `targetPortID`, etc., can be updated at the runtime.

The following code example illustrates how to update a connector's source point, target point, styles properties at runtime.

{% tab template= "diagram/connectors", es5Template="es5Connectorsupdate" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel = [{
    id: "connector1",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');
// Update the connector properties at the run time
diagram.connectors[0].style.strokeColor = '#6BA5D7';
diagram.connectors[0].style.fill = '#6BA5D7';
diagram.connectors[0].style.strokeWidth = 2;
diagram.connectors[0].targetDecorator.style.fill = '#6BA5D7';
diagram.connectors[0].targetDecorator.style.strokeColor = '#6BA5D7';
diagram.connectors[0].sourcePoint.x = 150;
diagram.connectors[0].targetPoint.x = 150;
diagram.dataBind();

```

{% endtab %}

## Connect nodes

* The [`sourceID`](../api/diagram/connector#sourceid-string) and [`targetID`](../api/diagram/connector#targetid-string) properties allow to define the nodes to be connected.

* The following code example illustrates how to connect two nodes.

{% tab template= "diagram/connectors", es5Template="es5ConnectNode" %}

```typescript

import {Diagram,NodeModel,ConnectorModel} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: 'Start',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 100,
        annotations: [{
            id: 'label1',
            content: 'Start'
        }],
        shape: {
            type: 'Flow',
            shape: 'Terminator'
        }
    },
    {
        id: 'Init',
        width: 140,
        height: 50,
        offsetX: 300,
        offsetY: 300,
        shape: {
            type: 'Flow',
            shape: 'Process'
        },
        annotations: [{
            content: 'var i = 0;'
        }]
    }
];
let connectors: ConnectorModel = {
    // Name of the connector
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // ID of the source and target nodes
    sourceID: "Start",
    targetID: "Init",
    type: 'Orthogonal'
};

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    connectors: [connectors],
    // Defines the default properties for the node
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});

diagram.appendTo('#element');

```

{% endtab %}

* When you remove NodeConstraints [`InConnect`](../api/diagram/nodeConstraints) from Default, the node accepts only an outgoing connection to dock in it. Similarly, when you remove NodeConstraints [`OutConnect`](../api/diagram/nodeConstraints) from Default, the node accepts only an incoming connection to dock in it.

* When you remove both InConnect and OutConnect NodeConstraints from Default, the node restricts connector to establish connection in it.

* The following code illustrates how to disable InConnect constraints.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     nodes:[
         {
            id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 150,
            shape: { type: 'Basic', shape: 'Rectangle' },
            //Disable InConnect constraints
            constraints: NodeConstraints.Default & ~NodeConstraints.InConnect,
         }
     ]
});
diagram.appendTo('#diagram');

```

## Connections with ports

The [`sourcePortID`](../api/diagram/connector#sourceportid-string) and [`targetPortID`](../api/diagram/connector#targetportid-string) properties allow to create connections between some specific points of source/target nodes.
The following code example illustrates how to create port to port connections.

{% tab template= "diagram/connectors", es5Template="es5Connectorsport" %}

```typescript

import {ConnectorModel,NodeModel,BasicShapeModel,PointPortModel,Diagram,PortVisibility} from'@syncfusion/ej2-diagrams';

let port1: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port1.shape = 'Circle';
port1.id = 'nodeportnew'
port1.visibility = PortVisibility.Visible
port1.id = 'port';
port1.offset = {
    x: 1,
    y: 1
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port2.offset = {
    x: 1,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';
let port3: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port3.offset = {
    x: 0,
    y: 1
};
port3.id = 'newnodeport1';
port3.visibility = PortVisibility.Visible
port3.shape = 'Circle';
let nodes: NodeModel[] = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [port1]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2, port3]
    },
];

let connectors: ConnectorModel = {
    id: "connector1",
    sourcePoint: {
        x: 100,
        y: 100
    },
    type: 'Orthogonal',
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}

let diagram: Diagram = new Diagram({
    width: 900,
    height: 900,
    nodes: nodes,
    connectors: [connectors],
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');
```

{% endtab %}

Similarly, the `sourcePortID` or `targetPortID` can be changed at the runtime by changing the port [`sourcePortID`](../api/diagram/connector#sourceportid-string) or [`targetPortID`](../api/diagram/connector#targetportid-string).

{% tab template= "diagram/connectors", es5Template="es5Connectorsportupdate" %}

```typescript

import {ConnectorModel,NodeModel,BasicShapeModel,PointPortModel,Diagram,PortVisibility} from'@syncfusion/ej2-diagrams';

let port1: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port1.shape = 'Circle';
port1.id = 'nodeportnew'
port1.visibility = PortVisibility.Visible
port1.id = 'port';
port1.offset = {
    x: 1,
    y: 1
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port2.offset = {
    x: 1,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';
let port3: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
port3.offset = {
    x: 0,
    y: 1
};
port3.id = 'newnodeport1';
port3.visibility = PortVisibility.Visible
port3.shape = 'Circle';
let nodes: NodeModel[] = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [port1]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2, port3]
    },
];

let connectors: ConnectorModel = {
    id: "connector1",
    sourcePoint: {
        x: 100,
        y: 100
    },
    type: 'Orthogonal',
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}

let diagram: Diagram = new Diagram({
    width: 900,
    height: 900,
    nodes: nodes,
    connectors: [connectors],
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');
// Update the target portID at the run time
diagram.connectors[0].targetPortID = 'newnodeport1'

```

{% endtab %}

* When you set PortConstraints to [`InConnect`](../api/diagram/portConstraints), the port accepts only an incoming connection to dock in it. Similarly, when you set PortConstraints to [`OutConnect`](../api/diagram/portConstraints), the port accepts only an outgoing connection to dock in it.

* When you set PortConstraints to None, the port restricts connector to establish connection in it.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     nodes:[
         {
            id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 150,
            shape: { type: 'Basic', shape: 'Rectangle' },
            ports: [
             //Enable portConstraints Inconnect
             { id: 'port', height: 10, width: 10, offset: { x: 1, y: 0.5 }, constraints: PortConstraints.InConnect },
           ]
         }
     ]
});
diagram.appendTo('#diagram');

```

## Segments

The path of the connector is defined with a collection of segments. There are three types of segments.

## Straight

To create a straight line, specify the [`type`](../api/diagram/segments) of the segment as **straight** and add a straight segment to [`segments`](../api/diagram/connector#segments) collection and need to specify [`type`](../api/diagram/connector#type-Segments) for the connector. The following code example illustrates how to create a default straight segment.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsSegments" %}

```typescript

import {Diagram,ConnectorModel,StraightSegmentModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = {
    id: "connector1",
    type: 'Straight',
    segments: [{
        // Defines the segment type of the connector
        type: 'Straight'
    }],
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: [connectors],
});

diagram.appendTo('#element');

```

{% endtab %}

The [`point`](../api/diagram/straightSegment#point-PointModel) property of straight segment allows you to define the end point of it. The following code example illustrates how to define the end point of a straight segment.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsSegmentsPoints" %}

```typescript

import {Diagram,ConnectorModel,StraightSegmentModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = {
    id: "connector1",
    // Defines the segment type of the connector
    segments: [{
        type: 'Straight',
        // Defines the point of the segment
        point: {
            x: 100,
            y: 150
        }
    }],
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: [connectors],
});

diagram.appendTo('#element');

```

{% endtab %}

## Orthogonal

Orthogonal segments is used to create segments that are perpendicular to each other.

Set the segment [`type`](../api/diagram/segments) as orthogonal to create a default orthogonal segment and need to specify [`type`](../api/diagram/connector#type-Segments). The following code example illustrates how to create a default orthogonal segment.

Multiple segments can be defined one after another. To create a connector with multiple segments, define and add the segments to [`connector.segments`](../api/diagram/connector#segments) collection. The following code example illustrates how to create a connector with multiple segments.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsOrtho" %}

```typescript

import {
    Diagram,
    ConnectorModel,
    OrthogonalSegmentModel
} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel[] = [{
        id: "connector1",
        // Define the type of the segment
        type: 'Orthogonal',
        segments: [{
            type: 'Orthogonal'
        }],
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        }
    },]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

The [`length`](../api/diagram/orthogonalSegment) and [`direction`](../api/diagram/orthogonalSegment) properties allow to define the flow and length of segment. The following code example illustrates how to create customized orthogonal segments.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsOrthoSegments" %}

```typescript

import {Diagram,ConnectorModel,OrthogonalSegmentModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = [{
        id: "connector1",
        type: 'Orthogonal',
        segments: [{
            type: 'Orthogonal',
            // Defines the direction for the segment lines
            direction: 'Right',
            // Defines the length for the segment lines
            length: 50
        }],
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        }
    },
    {
        id: "connector2",
        type: 'Orthogonal',
        // Defines multile segemnts for the connectors
        segments: [{
                type: 'Orthogonal',
                direction: 'Bottom',
                length: 150
            },
            {
                type: 'Orthogonal',
                direction: 'Right',
                length: 150
            }
        ],
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        sourcePoint: {
            x: 300,
            y: 100
        },
        targetPoint: {
            x: 400,
            y: 200
        }
    }
]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

>Note: You need to mention the segment type as same as what you mentioned in connector type. There should be no contradiction between connector type and segment type.

## Avoid overlapping

Orthogonal segments are automatically re-routed, in order to avoid overlapping with the source and target nodes. The following preview illustrates how orthogonal segments are re-routed.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsOverlapping" %}

```typescript

import {ConnectorModel,NodeModel,BasicShapeModel,PointPortModel,Diagram,PortVisibility} from '@syncfusion/ej2-diagrams';

let nodeport: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
};
nodeport.shape = 'Circle';
nodeport.visibility = PortVisibility.Visible
nodeport.id = 'port';
nodeport.offset = {
    x: 0,
    y: 0.5
};
let port2: PointPortModel = {
    style: {
        strokeColor: '#366F8C',
        fill: '#366F8C'
    }
}
port2.offset = {
    x: 0,
    y: 0.5
};
port2.id = 'port1';
port2.visibility = PortVisibility.Visible
port2.shape = 'Circle';
let nodes: NodeModel[] = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        ports: [nodeport]
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        ports: [port2]
    },
];

let connectors: ConnectorModel = {
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Orthogonal',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceID: 'node',
    targetID: 'node1',
    sourcePortID: 'port',
    targetPortID: 'port1'
}

let diagram: Diagram = new Diagram({
    width: 900,
    height: 900,
    nodes: nodes,
    connectors: [connectors],
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');

```

{% endtab %}

## Bezier

Bezier segments are used to create curve segments and the curves are configurable either with the control points or with vectors.

To create a bezier segment, the [`segment.type`](../api/diagram/segments) is set as `bezier` and need to specify [`type`](../api/diagram/connector#type-Segments) for the connector. The following code example illustrates how to create a default bezier segment.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsBezier" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel[] = [

    {
        id: 'connector1',
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        type: 'Bezier',
        segments: [{
            // Defines the type of the segment
            type: 'Bezier',
        }],
        sourcePoint: {
            x: 50,
            y: 100
        },
        targetPoint: {
            x: 150,
            y: 200
        },
    },
];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

The [`point1`](../api/diagram/bezierSegment#point1-PointModel) and [`point2`](../api/diagram/bezierSegment#point2-PointModel) properties of bezier segment enable you to set the control points. The following code example illustrates how to configure the bezier segments with control points.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsBezierPoints" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel[] = [

    {
        id: 'connector3',
        type: 'Bezier',
        style: {
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            strokeWidth: 2
        },
        targetDecorator: {
            style: {
                fill: '#6BA5D7',
                strokeColor: '#6BA5D7'
            }
        },
        segments: [{
            type: 'Bezier',
            // First control point: an absolute position from the page origin
            point1: {
                x: 100,
                y: 100
            },
            // Second control point: an absolute position from the page origin
            point2: {
                x: 200,
                y: 200
            }
        }],
        sourcePoint: {
            x: 100,
            y: 200
        },
        targetPoint: {
            x: 200,
            y: 100
        },
    },
];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

The [`vector1`](../api/diagram/bezierSegment#vector1-VectorModel) and [`vector2`](../api/diagram/bezierSegment#vector2-VectorModel) properties of bezier segment enable you to define the vectors. The following code illustrates how to configure a bezier curve with vectors.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsBezierVector" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel[] = [{
    id: 'connector2',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Defines the type of the segment
    type: 'Bezier',
    segments: [{
        type: 'Bezier',
        // Length and angle between the source point and the first control point
        vector1: {
            distance: 100,
            angle: 90
        },
        // Length and angle between the target point and the second control point
        vector2: {
            distance: 45,
            angle: 270
        }
    }],
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
}, ];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

## Decorator

* Starting and ending points of a connector can be decorated with some customizable shapes like arrows, circles, diamond, or path. The connection end points can be decorated with the [`sourceDecorator`](../api/diagram/connector#sourcedecorator-DecoratorModel) and [`targetDecorator`](../api/diagram/connector#targetdecorator-DecoratorModel) properties of the connector.

* The [`shape`](../api/diagram/decoratorShapes) property of `sourceDecorator` allows to define the shape of the decorators. Similarly, the [shape](../api/diagram/decoratorShapes) property of `targetDecorator` allows to define the shape of the decorators.

* To create custom shape for source decorator, use [`pathData`](../api/diagram/decorator#pathdata-string) property. Similarly, to create custom shape for target decorator, use [`pathData`](../api/diagram/decorator#pathData-string) property.

* The following code example illustrates how to create decorators of various shapes.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsDecorator" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel = {
    id: "connector1",
    type: 'Straight',
    // Decorator shape- circle
    sourceDecorator: {
        shape: 'Circle',
        // Defines the style for the sourceDecorator
        style: {
            // Defines the strokeWidth for the sourceDecorator
            strokeWidth: 3,
            // Defines the strokeColor for the sourceDecorator
            strokeColor: 'red'
        },

    },
    // Decorator shape - Diamond
    targetDecorator: {
        // Defines the custom shape for the connector's target decorator
        shape: 'Custom',
        //Defines the  path for the connector's target decorator
        pathData: 'M80.5,12.5 C80.5,19.127417 62.59139,24.5 40.5,24.5 C18.40861,24.5 0.5,19.127417 0.5,12.5' +
            'C0.5,5.872583 18.40861,0.5 40.5,0.5 C62.59139,0.5 80.5,5.872583 80.5,12.5 z'
        //defines the style for the target decorator
        style: {
            // Defines the strokeWidth for the targetDecorator
            strokeWidth: 3,
            // Defines the strokeColor for the sourceDecorator
            strokeColor: 'green',
            // Defines the opacity for the sourceDecorator
            opacity: .8
        },
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};
let connectors2: ConnectorModel = {
    id: "connectors2",
    type: 'Straight',
    // Decorator shape - IndentedArrow
    sourceDecorator: {
        shape: 'IndentedArrow',
        style: {
            strokeWidth: 3,
            strokeColor: 'blue'
        },

    },
    // Decorator shape - OutdentedArrow
    targetDecorator: {
        shape: 'OutdentedArrow',
        style: {
            strokeWidth: 3,
            strokeColor: 'yellow'
        },
    },
    sourcePoint: {
        x: 400,
        y: 100
    },
    targetPoint: {
        x: 300,
        y: 200
    }
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: [connectors, connectors2],
});

diagram.appendTo('#element');

```

{% endtab %}

## Padding

Padding is used to leave the space between the Connector's end point and the object to where it is connected.

* The [`sourcePadding`](../api/diagram/connector#sourcepadding) property of connector defines space between the source point and the source node of the connector.

* The [`targetPadding`](../api/diagram/connector#targetpadding) property of connector defines space between the end point and the target node of the connector.

* The following code example illustrates how to leave space between the connection end points and source and target nodes.

{% tab template= "diagram/connectors", es5Template="es5Padding" %}

```typescript

import {ConnectorModel,NodeModel,BasicShapeModel,Diagram} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
    },
    {
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
    },
];

let connectors: ConnectorModel = {
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourceID: 'node',
    targetID: 'node1',
    // Set Source Padding value
    sourcePadding:20,
    // Set Target Padding value
    targetPadding:20
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: 900,
    nodes: nodes,
    connectors: [connectors],
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
});
diagram.appendTo('#element');

```

{% endtab %}

## Flip

The diagram Provides support to flip the connector. The [`flip`](../api/diagram/connector#flip) is performed to give the mirrored image of the original element.

The flip types are as follows:

* HorizontalFlip
 [`Horizontal`](../api/diagram/flipDirection) is used to interchange the connector source and target x points.

* VerticalFlip
[`Vertical`](../api/diagram/flipDirection) is used to interchange the connector source and target y points.

* Both
[`Both`](../api/diagram/flipDirection) is used to interchange the source point as target point and target point as source point
.
{% tab template= "diagram/connectors", es5Template="es5ConnectorsFilp" %}

```typescript

import {ConnectorModel,NodeModel,BasicShapeModel,Diagram} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = {
    id: "connector1",
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    type: 'Orthogonal',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    // Flip the connector in horizontal direction
    flip:"Horizontal"
}

let diagram: Diagram = new Diagram({
    width: '100%',
    height: 900,
    connectors: [connectors],
});
diagram.appendTo('#element');

```

{% endtab %}

 >Note: The flip is not applicable when the connectors connect in nodes

## Bridging

Line bridging creates a bridge for lines to smartly cross over the other lines, at points of intersection. By default, [`bridgeDirection`](../api/diagram#bridgeDirection-BridgeDirection) is set to top. Depending upon the direction given bridging direction appears.
Bridging can be enabled/disabled either with the `connector.constraints` or `diagram.constraints`. The following code example illustrates how to enable line bridging.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsBridging" %}

```typescript

import {Diagram,ConnectorBridging,DiagramConstraints,ConnectorModel,NodeModel}from'@syncfusion/ej2-diagrams';
Diagram.Inject(ConnectorBridging);

let node1: NodeModel = {
    id: 'Transaction',
    width: 150,
    height: 60,
    offsetX: 300,
    offsetY: 60,
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    },
    annotations: [{
        id: 'label1',
        content: 'Start Transaction',
        offset: {
            x: 0.5,
            y: 0.5
        }
    }],
};

let node2: NodeModel = {
    id: 'Verification',
    width: 150,
    height: 60,
    offsetX: 300,
    offsetY: 250,
    shape: {
        type: 'Flow',
        shape: 'Process'
    },
    annotations: [{
        id: 'label2',
        content: 'Verification',
        offset: {
            x: 0.5,
            y: 0.5
        }
    }]
};

let connectors: ConnectorModel = {
    id: 'connector1',
    type: 'Straight',
    sourceID: 'Transaction',
    targetID: 'Verification'
};
let connectors2: ConnectorModel = {
    id: 'connector2',
    type: 'Straight',
    sourcePoint: {
        x: 200,
        y: 130
    },
    targetPoint: {
        x: 400,
        y: 130
    }
};
let connector3: ConnectorModel = {
    id: 'connector3',
    type: 'Straight',
    sourcePoint: {
        x: 200,
        y: 170
    },
    targetPoint: {
        x: 400,
        y: 170
    }
};
// Enables bridging for every connector added in the model
let diagram: Diagram = new Diagram({
    width: '100%',
    getConnectorDefaults: (obj: ConnectorModel): ConnectorModel => {
        obj.style.strokeColor = '#6BA5D7';
        obj.style.fill = '#6BA5D7';
        obj.style.strokeWidth = 2;
        obj.targetDecorator.style.fill = '#6BA5D7';
        obj.targetDecorator.style.strokeColor = '#6BA5D7';
        return obj;
    },
    getNodeDefaults: (node: NodeModel) => {
        node.height = 100;
        node.width = 100;
        node.style.fill = '#6BA5D7';
        node.style.strokeColor = 'white';
        return node;
    },
    nodes: [node1, node2],
    height: '600px',
    // Enables the bridging constraints for the connector
    constraints: DiagramConstraints.Default | DiagramConstraints.Bridging,
    connectors: [connectors, connectors2, connector3]
});

diagram.appendTo('#element');

```

{% endtab %}
>Note: You need to inject connector bridging module into the diagram.

The [`bridgeSpace`](../api/diagram/connector#bridgespace-number) property of connectors can be used to define the width for line bridging.

Limitation: Bezier segments do not support bridging.

## Corner radius

Corner radius allows to create connectors with rounded corners. The radius of the rounded corner is set with the [`cornerRadius`](../api/diagram/connector#cornerradius-number) property.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsCornerRadius" %}

```typescript

import {Diagram,NodeModel,ConnectorModel} from '@syncfusion/ej2-diagrams';

let nodes: NodeModel[] = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 350,
    },
]

let connectors: ConnectorModel[] = [{
    id: "connector1",
    type: 'Orthogonal',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    // Sets the radius for the rounded corner
    cornerRadius: 10,
    sourceID: 'node1',
    targetID: 'node2',
    segments: [{
        type: 'Orthogonal',
        direction: 'Right',
        length: 50
    }],
}]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
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

```

{% endtab %}

## Appearance

* The connector’s [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number), [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string), and [`opacity`](../api/diagram/strokeStyle#opacity-number) properties are used to customize the appearance of the connector segments.

* The [`visible`](../api/diagram/connector#visible-boolean) property of the connector enables or disables the visibility of connector.

* Default values for all the `connectors` can be set using the `getConnectorDefaults` properties. For example, if all connectors have the same type or having the same property then such properties can be moved into `getConnectorDefaults`.

## Segment appearance

The following code example illustrates how to customize the segment appearance.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsAppearance" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel[] = [{
        id: "connector1",
        targetDecorator: {
            style: {
                strokeColor: '#6BA5D7',
                fill: '#6BA5D7',
                strokeWidth: 2
            }
        },
        style: {
            // Stroke color
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            // Stroke width of the line
            strokeWidth: 2,
            // Line style
            strokeDashArray: '2,2'
        },
        sourcePoint: {
            x: 100,
            y: 100
        },
        targetPoint: {
            x: 200,
            y: 200
        },
        segments: [{
            type: 'Orthogonal',
            direction: 'Right',
            length: 50
        }],
    },
    {
        id: "connector2",
        // Set the visibility of the connector to false
        visible: false,
        targetDecorator: {
            style: {
                strokeColor: '#6BA5D7',
                fill: '#6BA5D7',
                strokeWidth: 2
            }
        },
        style: {
            // Stroke color
            strokeColor: '#6BA5D7',
            fill: '#6BA5D7',
            // Stroke width of the line
            strokeWidth: 2,
            // Line style
            strokeDashArray: '2,2'
        },
        sourcePoint: {
            x: 300,
            y: 300
        },
        targetPoint: {
            x: 400,
            y: 400
        },
        segments: [{
            type: 'Orthogonal',
            direction: 'Right',
            length: 50
        }],
    }
]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Define the default values for all the connector.Similary we can add all the properties
    getConnectorDefaults: (obj: ConnectorModel): ConnectorModel => {
        obj.type = 'Orthogonal'
        return obj;
    }
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

## Decorator appearance

* The source decorator’s [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number), and [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string) properties are used to customize the color, width, and appearance of the decorator.

* To set the border stroke color, stroke width, and stroke dash array for the target decorator, use [`strokeColor`](../api/diagram/strokeStyle#strokecolor-string), [`strokeWidth`](../api/diagram/strokeStyle#strokewidth-number), and [`strokeDashArray`](../api/diagram/strokeStyle#strokedasharray-string).

* To set the size for source and target decorator, use width and height property.

The following code example illustrates how to customize the appearance of the decorator.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsDecAppearance" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel[] = [{
    id: "connector1",
    type: 'Straight',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    bridgeSpace: 20,
    // Cutomize the target decorator
    targetDecorator: {
        style: {
            // Fill color of the decorator
            fill: '#6BA5D7',
            // Stroke color of the decorator
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};]

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
});

diagram.appendTo('#element');

```

{% endtab %}

## Interaction

* Diagram allows to edit the connectors at runtime. To edit the connector segments at runtime, refer to [`Connection Editing`](../api/diagram/connectorEditing).

## Automatic line routing

Diagram provides additional flexibility to re-route the diagram connectors. A connector will frequently re-route itself when a shape moves next to it. The following screenshot illustrates how the connector automatically re-routes the segments.  

* Dependency LineRouting module should be injected to the application as the following code snippet.

```javascript

/**
 * Injecting the automatic line routing module.
 */
ej.diagrams.Diagram.Inject(ej.diagrams.LineRouting);

```

* Now, the line routing constraints must be included to the default diagram constraints to enable automatic line routing support like below.

```javascript
/**
 *  Initialize the Diagram
 */
   var diagram = new ej.diagrams.Diagram({
         //Add Line routing constraints to diagram.
        constraints: ej.diagrams.DiagramConstraints.Default |
                    ej.diagrams.DiagramConstraints.LineRouting
    });
    diagram.appendTo('#diagram');

```

* The following code block shows how to create the diagram with specifying nodes, connectors, constraints, and necessary modules for line routing.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsLineRouting" %}

```typescript

import {
  Diagram, SnapConstraints, LineRouting, DiagramConstraints, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
Diagram.Inject(LineRouting);


let nodes: NodeModel[] = [
  { id: 'shape1', offsetX: 100, offsetY: 100, width: 120, height: 50 },
  { id: 'shape2', offsetX: 300, offsetY: 300, width: 120, height: 50 },
  { id: 'shape3', offsetX: 150, offsetY: 200, width: 120, height: 50 }
];
let connectors: ConnectorModel[] = [
  { id: 'connector', sourceID: 'shape1', targetID: 'shape2', type: 'Orthogonal' }
];

//initialize the diagram control
let diagram: Diagram = new Diagram({
  width: '100%', height: 900, nodes: nodes, connectors: connectors,
  //Add Line routing constraints to diagram.
  constraints: DiagramConstraints.Default | DiagramConstraints.LineRouting,
  getNodeDefaults: function (node) {
    node = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } }
    return node;
  },
  snapSettings: {
    constraints: SnapConstraints.None,
  }
});
diagram.appendTo('#element');

```

{% endtab %}

* In some situations, automatic line routing enabled diagram needs to ignore a specific connector from automatic line routing. So, in this case, auto routing feature can be disabled to the specific connector using the [`constraints`](../api/diagram/connector#constraints-ConnectorConstraints) property of the connector like the following code snippet.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsLineRoutingDisable" %}

```typescript

import {
  Diagram, SnapConstraints,ConnectorConstraints, LineRouting, DiagramConstraints, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
Diagram.Inject(LineRouting);


let nodes: NodeModel[] = [
 { id: 'shape1', offsetX: 100, offsetY: 100, width: 120, height: 50 },
  { id: 'shape2', offsetX: 350, offsetY: 300, width: 120, height: 50 },
  { id: 'shape3', offsetX: 150, offsetY: 200, width: 120, height: 50 },
    { id: 'shape4', offsetX: 300, offsetY: 200, width: 120, height: 50 }
];
let connectors: ConnectorModel[] = [
  { id: 'connector', sourceID: 'shape1', targetID: 'shape2', type: 'Orthogonal',annotations:[{offset:.7,content:' Routing \n enabled',style:{fill:"white"}}]},
  { id: 'connector2', sourceID: 'shape1', targetID: 'shape2',annotations:[{offset:.6,content:' Routing \n disabled',style:{fill:"white"}}], type: 'Orthogonal', constraints: ConnectorConstraints.Default &~ ConnectorConstraints.InheritLineRouting }
];

//initialize the diagram control
let diagram: Diagram = new Diagram({
  width: '100%', height: 900, nodes: nodes, connectors: connectors,
  //Add Line routing constraints to diagram.
  constraints: DiagramConstraints.Default | DiagramConstraints.LineRouting,
  getNodeDefaults: function (node) {
    node = { style: { strokeColor: '#6BA5D7', fill: '#6BA5D7' } }
    return node;
  },
  snapSettings: {
    constraints: SnapConstraints.None,
  }
});

diagram.appendTo('#element');

```

{% endtab %}

## Constraints

* The [`constraints`](../api/diagram/connector#constraints-ConnectorConstraints) property of connector allows to enable/disable certain features of connectors.

* To enable or disable the constraints, refer [`constraints`](../api/diagram/connectorConstraints).

The following code illustrates how to disable selection.

{% tab template= "diagram/connectors", es5Template="es5ConnectorsConstraints" %}

```typescript

import {Diagram,DiagramConstraints,ConnectorConstraints,ConnectorModel} from '@syncfusion/ej2-diagrams';


let connectors: ConnectorModel = {
    id: "connector1",
    // Disables selection constraints
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.Select,
    type: 'Straight',
    style: {
        strokeColor: '#6BA5D7',
        fill: '#6BA5D7',
        strokeWidth: 2
    },
    targetDecorator: {
        style: {
            fill: '#6BA5D7',
            strokeColor: '#6BA5D7'
        }
    },
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};



let diagram: Diagram = new Diagram({
    width: 1500,
    height: 1500,
    connectors: [connectors]
});

diagram.appendTo('#element');

```

{% endtab %}

## Custom properties

* The [`addInfo`](../api/diagram/connector#addinfo-Object) property of connectors allow you to maintain additional information to the connectors.

```javascript

let connectors: ConnectorModel = {
    id: 'connector1',
    // Defines the information about the connector
    addInfo:'centralconnector',
    type: 'Straight',
    sourceID: 'Transaction',
    targetID: 'Verification'
};

```

## Stack order

The connectors [`zIndex`](../api/diagram/connector#zindex-number) property specifies the stack order of the connector. A connector with greater stack order is always in front of a connector with a lower stack order.

The following code illustrates how to render connector based on the stack order.

{% tab template= "diagram/connectors", es5Template="es5zindex" %}

```typescript

import {Diagram,ConnectorModel} from '@syncfusion/ej2-diagrams';

let connectors: ConnectorModel = {
    id: 'connector1',
    // Defines the z-index value for the connector
    zIndex: 2,
    type: 'Straight',
    sourcePoint: {
        x: 300,
        y: 100
    },
    targetPoint: {
        x: 300,
        y: 200
    }
};
let connectors2: ConnectorModel = {
    id: 'connector2',
    type: 'Straight',
    // Defines the z-index value for the connector
    zIndex: 1,
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};

let diagram: Diagram = new Diagram({
    width: '100%',
    getConnectorDefaults: (obj: ConnectorModel): ConnectorModel => {
        obj.style.strokeColor = '#6BA5D7';
        obj.style.fill = '#6BA5D7';
        obj.style.strokeWidth = 2;
        obj.targetDecorator.style.fill = '#6BA5D7';
        obj.targetDecorator.style.strokeColor = '#6BA5D7';
        return obj;
    },
    height: '600px',
    connectors: [connectors, connectors2]
});

diagram.appendTo('#element');

```

{% endtab %}

## See Also

* [How to add annotations to the connector](./labels)
* [How to enable/disable the behavior of the node](./constraints)
* [How to add connectors to the symbol palette](./symbol-palette)
* [How to perform the interaction on the connector](./interaction#connection-editing)
* [How to create diagram connectors using drawing tools](./tools)