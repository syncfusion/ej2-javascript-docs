---
title: "Layers"
component: "Diagram"
description: "Layer is used to organize the shapes on the diagram control"
---

# Layers

**Layer** is used to organize related shapes on a diagram control. A layer is a named category of shapes. By assigning shapes to different layers, you can selectively view, remove, and lock different categories of shapes.

In diagram, [Layers](../api/diagram) provide a way to change the properties of all shapes that have been assigned to that layer. The following properties can be set.

* Visible
* Lock
* Objects
* AddInfo

## Visible

The layer's [visible](../api/diagram/layer#visible-boolean) property is used to control the visibility of the elements assigned to the layer.

```javascript

ej.diagrams.Diagram.Inject(ej.diagrams.Diagram, ej.diagrams.ConnectorModel,ej.diagrams.NodeModel,ej.diagrams.LayerModel);

// A node is created and stored in nodes array.

var nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        annotations: [{
            content: 'Default Shape'
        }]
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        shape: {
            type: 'Path',
            data: 'M540.3643,137.9336L546.7973,159.7016L570.3633,159.7296L550.7723,171.9366L558.9053,194.9966L540.3643,' +
                '179.4996L521.8223,194.9966L529.9553,171.9366L510.3633,159.7296L533.9313,159.7016L540.3643,137.9336z'
        },
        annotations: [{
            content: 'Path Element'
        }]
    }
];

var connectors = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 300
    },
    targetPoint: {
        x: 200,
        y: 400
    },
}];

// initialize diagram component

var diagram = new ej.diagrams.Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
    nodes: nodes,
    layers: [{
            id: 'layer1',
            visible: true,
            objects: ['node1']
        }
    ]
},'#element');

```

## Lock

The layer's [lock](../api/diagram/layer#lock-boolean) property is used to prevent or allow changes to the elements dimension and position.

```javascript

ej.diagrams.Diagram.Inject(ej.diagrams.Diagram, ej.diagrams.ConnectorModel,ej.diagrams.NodeModel,ej.diagrams.LayerModel);

// A node is created and stored in nodes array.

var nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        annotations: [{
            content: 'Default Shape'
        }]
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        shape: {
            type: 'Path',
            data: 'M540.3643,137.9336L546.7973,159.7016L570.3633,159.7296L550.7723,171.9366L558.9053,194.9966L540.3643,' +
                '179.4996L521.8223,194.9966L529.9553,171.9366L510.3633,159.7296L533.9313,159.7016L540.3643,137.9336z'
        },
        annotations: [{
            content: 'Path Element'
        }]
    }
];

var connectors = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 300
    },
    targetPoint: {
        x: 200,
        y: 400
    },
}];

// initialize diagram component

var diagram = new ej.diagrams.Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
    nodes: nodes,
    layers: [{
            id: 'layer1',
            visible: true,
            objects: ['node1'],
            lock: true
        },
        {
            id: 'layer2',
            visible: true,
            objects: ['node2'],
            lock: false
        }
    ]
},'#element');

```

## Objects

The layer's [objects](../api/diagram/layer#objects-string[]) property defines the diagram elements to the layer.

```javascript

ej.diagrams.Diagram.Inject(ej.diagrams.Diagram, ej.diagrams.ConnectorModel,ej.diagrams.NodeModel,ej.diagrams.LayerModel);

// A node is created and stored in nodes array.

var nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        annotations: [{
            content: 'Default Shape'
        }]
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        shape: {
            type: 'Path',
            data: 'M540.3643,137.9336L546.7973,159.7016L570.3633,159.7296L550.7723,171.9366L558.9053,194.9966L540.3643,' +
                '179.4996L521.8223,194.9966L529.9553,171.9366L510.3633,159.7296L533.9313,159.7016L540.3643,137.9336z'
        },
        annotations: [{
            content: 'Path Element'
        }]
    }
];

var connectors = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 300
    },
    targetPoint: {
        x: 200,
        y: 400
    },
}];

// initialize diagram component

var diagram = new ej.diagrams.Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
    nodes: nodes,
    layers: [{
            id: 'layer1',
            visible: true,
            objects: ['node1', 'node2']
        },
        {
            id: 'layer2',
            visible: true,
            objects: ['node2']
        }
    ]
},'#element');

```

## AddInfo

The [`addInfo`](../api/diagram/layer#addinfo-Object) property of layers allow you to maintain additional information to the layers.

The following code illustrates how to add additional information to the layers.

```javascript

ej.diagrams.Diagram.Inject(ej.diagrams.Diagram, ej.diagrams.ConnectorModel,ej.diagrams.NodeModel,ej.diagrams.LayerModel);

// A node is created and stored in nodes array.

var nodes = [{
        id: 'node1',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        annotations: [{
            content: 'Default Shape'
        }]
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100,
        shape: {
            type: 'Path',
            data: 'M540.3643,137.9336L546.7973,159.7016L570.3633,159.7296L550.7723,171.9366L558.9053,194.9966L540.3643,' +
                '179.4996L521.8223,194.9966L529.9553,171.9366L510.3633,159.7296L533.9313,159.7016L540.3643,137.9336z'
        },
        annotations: [{
            content: 'Path Element'
        }]
    }
];

var connectors = [{
    id: 'connector1',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 300
    },
    targetPoint: {
        x: 200,
        y: 400
    },
}];

var addInfo = { Description: 'Layer1' };

// initialize Diagram component

var diagram = new ej.diagrams.Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
    nodes: nodes,
    layers: [{
            id: 'layer1',
            visible: true,
            objects: ['node1', 'node2'],
            addInfo: addInfo
        },
        {
            id: 'layer2',
            visible: true,
            objects: ['node2']
        }
    ]
});

```

### Add layer at runtime

Layers can be added at runtime by using the [`addLayer`](../api/diagram#addLayer) public method.

The layer's [`ID`](../api/diagram/layer#id-string) property defines the ID of the layer, and its further used to find the layer at runtime and do any customization.

The following code illustrates how to add a layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// add the layers to the existing diagram layer collection
diagram.addLayer({
    id: 'newlayer',
    objects: [],
    visible: true,
    lock: false,
    zIndex: -1
}, [{
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 300
    },
    targetPoint: {
        x: 200,
        y: 400
    }
}]);

```

### Remove layer at runtime

Layers can be removed at runtime by using the [`removeLayer`](../api/diagram#removeLayer) public method.

The following code illustrates how to remove a layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// remove the diagram layers
diagram.removeLayer([diagram.model.layers[i]]);

```

### moveObjects

Objects of the layers can be moved by using the [`moveObjects`](../api/diagram#moveObjects) public method.

The following code illustrates how to move objects from one layer to another layer from the diagram.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// move the objects of diagram layers
diagram.moveObjects(['connector1'], 'layer2');

```

### bringLayerForward

Layers can be moved forward at runtime by using the [`bringLayerForward`](../api/diagram#bringLayerForward) public method.

The following code illustrates how to bring forward to layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// move the layer forward
diagram.bringLayerForward('layer1');

```

### sendLayerBackward

Layers can be moved backward at runtime by using the [`sendLayerBackward`](../api/diagram#sendLayerBackward) public method.

The following code illustrates how to send backward to layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// move the layer backward
diagram.sendLayerBackward('layer1');

```

### cloneLayer

Layers can be cloned with its object by using the [`cloneLayer`](../api/diagram#cloneLayer) public method.

The following code illustrates how to bring forward to layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram = diagramElement.ej2_instances[0];
// clone a layer with its object
diagram.cloneLayer('layer2');

```

### getActiveLayer

To get the active layers back in diagram, use the [`getActiveLayer`](../api/diagram#getActiveLayer) public method.

The following code illustrates how to bring forward to layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram: Object[] = diagramElement.ej2_instances[0];
// gets the active layer back
diagram.getActiveLayer();

```

### setActiveLayer

Set the active layer by using the [`setActiveLayer`](../api/diagram#setActiveLayer) public method.

The following code illustrates how to bring forward to layer.

```javascript

var diagramElement = document.getElementById('element');
var diagram: Object[] = diagramElement.ej2_instances[0];
// set the active layer
//@param layerName defines the name of the layer which is to be active layer
diagram.setActiveLayer('layer2');

```