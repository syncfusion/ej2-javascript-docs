---
title: "API Migration"
component: "Diagram"
description: "This article describes the API migration process of Diagram component from Essential JS 1 to Essential JS 2."
---

# Migration from Essential JS 1

This article describes the API migration process of Diagram component from Essential JS 1 to Essential JS 2.

## Background

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the background color of diagram elements</b></td>

<td><b>Property</b>:<i>`backgroundColor`</i>
<code>
$("#diagram").ejDiagram({
    backgroundColor: "red"
});
</code>
</td>

<td><b>Property</b>:<i>`backgroundColor`</i>
<code>
var diagram = new ej.diagrams.Diagram({
    backgroundColor: 'red'
});
diagram.appendTo('#diagram');
</code>
</td>
</tr>

<tr>
<td><b>Defines how to align the background image over the diagram area</b></td>
<td><b>Property</b>:<i>`backgroundImage.alignment`</i>
<code>
$("#diagramcontent").ejDiagram({
    backgroundImage: {
        alignment: ej.datavisualization.Diagram.ImageAlignment.XMidYMid
    }
});
</code>
</td>

<td><b>Property</b>:<i>`background.align`</i>
<code>
var diagram = new ej.diagrams.Diagram({
    pageSettings: {
        background: {
            align: 'XMidYMid'
        }
    }
});
diagram.appendTo('#diagram');
</code>
</td>
</tr>

<tr>
<td><b>Defines how the background image should be scaled/stretched</b></td>

<td><b>Property</b>:<i>`backgroundImage.scale`</i>
<code>
$("#diagramcontent").ejDiagram({
    backgroundImage: {
        scale: ej.datavisualization.Diagram.ScaleConstraints.Meet
    }
});
</code>
</td>

<td><b>Property</b>:<i>`background.scale`</i>
<code>
var diagram = new ej.diagrams.Diagram({
    pageSettings: {
        background: {
            scale: 'Meet'
        }
    }
});
diagram.appendTo('#diagram');
</code>
</td>
</tr>

<tr>
<td><b>Sets the source path of the background image</b></td>

<td><b>Property</b>:<i>`backgroundImage.source`</i>
<code>
$("#diagramcontent").ejDiagram({
    backgroundImage: {
        source: "Syncfusion.png"
    }
});
</code>
</td>

<td><b>Property</b>:<i>`background.source`</i>
<code>
var diagram = new ej.diagrams.Diagram({
    pageSettings: {
        background: {
            source: 'Syncfusion.png'
        }
    }
});
diagram.appendTo('#diagram');
</code>
</td>
</tr>
</table>

## Bridging

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Sets the direction of line bridges</b></td>

<td><b>Property</b>:<i>`bridgeDirection`</i>
<code>
$("#diagramcontent").ejDiagram({
    bridgeDirection: ej.datavisualization.Diagram.BridgeDirection.Bottom
});
</code>
</td>

<td><b>Property</b>:<i>`bridgeDirection`</i>
<code>
var diagram = new ej.diagrams.Diagram({
    bridgeDirection: 'Top'
});
diagram.appendTo('#diagram');
</code>
</td>
</tr>
</table>

## CommandManager

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Stores the multiple command names with the corresponding command objects</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>The command is executable at the moment or not.
</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.canExecute`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.canExecute`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines what to be executed when the key combination is recognized
</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.execute`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.execute`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines a combination of keys and key modifiers, on recognition of which the command will be executed</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the key value, on recognition of which the command will be executed
</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture.key`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture.key`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets a combination of key modifiers, on recognition of which the command will be executed.
</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture.keyModifiers`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.gesture.keyModifiers`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines any additional parameters that are required at runtime
</b></td>
<td>
<b>Property</b>:<i>`commandManager.commands.parameter`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    commandManager: {
        commands: {
            "clone": {
                parameter : "node",
                gesture: {
                    key: ej.datavisualization.Diagram.Keys.C,
                    keyModifiers: ej.datavisualization.Diagram.KeyModifiers.Shift
                },
                canExecute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    return diagram.model.selectedItems.children.length;
                },
                execute: function(args) {
                    var diagram = $("#diagramcontent").ejDiagram("instance");
                    diagram.copy();
                    diagram.paste();
                }
            }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`commandManager.commands.parameter`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    commandManager: {
        commands: [{
            name: 'customCopy',
            parameter: 'node',
            canExecute: function() {
                if (diagram.selectedItems.nodes.length > 0 || diagram.selectedItems.connectors.length > 0) {
                    return true;
                }
                return false;
            },
            execute: function() {
                for (var i = 0; i < diagram.selectedItems.nodes.length; i++) {
                    diagram.selectedItems.nodes[i].style.fill = 'red';
                }
                diagram.dataBind();
            },
            gesture: {
                key: Keys.G,
                keyModifiers: KeyModifiers.Shift
            }
        }]
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## Connectors

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allows the user to save custom information/data about a connector</b></td>
<td>
<b>Property</b>:<i>`connectors.addInfo`</i>
</br>
</br>
<code>
var addInfo = {
    Description: "Bidirectional Flow"
};
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    addInfo: addInfo
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.addInfo`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the bridgeSpace of connector</b></td>
<td>
<b>Property</b>:<i>`connectors.bridgeSpace`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    bridgeSpace: 15,
    targetPoint: {
        x: 200,
        y: 200
    },
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.bridgeSpace`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    bridgeSpace: 15,
    targetPoint: {
        x: 600,
        y: 200
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables or disables the behaviors of connectors</b></td>
<td>
<b>Property</b>:<i>`connectors.constraints`</i>
</br>
</br>
<code>
var ConnectorConstraints = ej.datavisualization.Diagram.ConnectorConstraints;
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.Select
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.constraints`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    constraints: ConnectorConstraints.Default | ConnectorConstraints.Drag
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the radius of the rounded corner</b></td>
<td>
<b>Property</b>:<i>`connectors.cornerRadius`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    cornerRadius: 10, segments:[{ type: "orthogonal"}]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.cornerRadius`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    cornerRadius: 10,
    type: 'Orthogonal',
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Customize connectors appearance using user-defined CSS</b></td>
<td>
<b>Property</b>:<i>`connectors.cssClass`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    cssClass: "hoverConnector"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the connector</b></td>
<td>
<b>Property</b>:<i>`connectors.horizontalAlign`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    horizontalAlign:ej.datavisualization.Diagram.HorizontalAlignment.Right
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A collection of JSON objects where each object represents a label</b></td>
<td>
<b>Property</b>:<i>`connectors.labels`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    labels:[{ text:"connector" }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.annotations`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    annotations: [{
        id: 'label',
        content: 'Text',
        offset: 0.5
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Stroke color of the connector</b></td>
<td>
<b>Property</b>:<i>`connectors.lineColor`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    lineColor: "blue"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>

<td>
<b>Property</b>:<i>`connectors.style.strokeColor`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    style: {
        strokeColor: 'blue'
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</tr>

<tr>
<td><b>Sets the pattern of dashes and gaps used to stroke the path of the connector</b></td>
<td>
<b>Property</b>:<i>`connectors.lineDashArray`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    lineColor: "blue",
    lineDashArray: "2,2"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.style.strokeDashArray`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    style: {
        strokeColor: 'blue',
        strokeWidth: 3,
        strokeDashArray: '2,2'
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the width of the line</b></td>
<td>
<b>Property</b>:<i>`connectors.lineWidth`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    lineWidth: 10
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.style.strokeWidth`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    style: {
        strokeColor: 'blue',
        strokeWidth: 3,
        strokeDashArray: '2,2'
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the padding value to ease the interaction with connectors
</b></td>
<td>
<b>Property</b>:<i>`connectors.lineHitPadding`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    linehitPadding: 15
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.hitPadding`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    hitPadding: 10
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the minimum space to be left between the bottom of parent bounds and the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.marginBottom`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    marginBottom: 15
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.margin.bottom`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    margin: {
        bottom: 3
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the minimum space to be left between the top of parent bounds and the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.marginTop`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    marginTop: 15
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.margin.top`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    margin: {
        top: 3
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the minimum space to be left between the left of parent bounds and the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.marginLeft`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    marginLeft: 15
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.margin.left`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    margin: {
        left: 3
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the minimum space to be left between the right of parent bounds and the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.marginRight`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    marginRight: 15
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td>
<td>
<b>Property</b>:<i>`connectors.margin.right`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    margin: {
        right: 3
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets a unique name for the connector</b></td>
<td>
<b>Property</b>:<i>`connectors.name`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.id`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the transparency of the connector</b></td>
<td>
<b>Property</b>:<i>`connectors.opacity`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    opacity: 0.5
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.style.opacity`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    style: {
        opacity: 0.5
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the parent name of the connector.
</b></td>
<td>
<b>Property</b>:<i>`connectors.parent`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    parent: "group"
};
var group = {
    name: "group",
    children: ["connector"]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [group]
});
</code>
</td><td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>An array of JSON objects where each object represents a segment
</b></td>
<td>
<b>Property</b>:<i>`connectors.segments`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "straight",
        point: {
            x: 75,
            y: 150
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
            type: 'Orthogonal',
            length: 30,
            direction: 'Bottom'
        },
        {
            type: 'Orthogonal',
            length: 80,
            direction: 'Right'
        }
    ]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the direction of orthogonal segment
</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.direction`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "straight",
        point: {
            x: 75,
            y: 150
        },
        direction: "bottom"
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.direction`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
            type: 'Orthogonal',
            length: 30,
            direction: 'Bottom'
        },
        {
            type: 'Orthogonal',
            length: 80,
            direction: 'Right'
        }
    ]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the length of orthogonal segment
</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.length`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "straight",
        point: {
            x: 75,
            y: 150
        },
        length: 50
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.length`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
            type: 'Orthogonal',
            length: 30,
            direction: 'Bottom'
        },
        {
            type: 'Orthogonal',
            length: 80,
            direction: 'Right'
        }
    ]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the end point of bezier/straight segment</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.point`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "straight",
        point: {
            x: 75,
            y: 150
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.point`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Straight',
        point: {
            x: 800,
            y: 50
        }
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the first control point of the bezier segment</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.point1`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "bezier",
        point1: {
            x: 150,
            y: 50
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.point1`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 600,
            y: 300
        },
        point1: {
            x: 525,
            y: 475
        }
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the second control point of bezier segment</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.point2`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "bezier",
        point1: {
            x: 150,
            y: 50
        },
        point2: {
            x: 150,
            y: 150
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.point2`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 600,
            y: 300
        },
        point1: {
            x: 525,
            y: 475
        },
        point2: {
            x: 575,
            y: 475
        }
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the type of the segment
</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.type`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: ej.datavisualization.Diagram.Segments.Bezier
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.type`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 600,
            y: 300
        },
        point1: {
            x: 525,
            y: 475
        },
        point2: {
            x: 575,
            y: 475
        }
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the length and angle between the first control point and the start point of bezier segment</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.vector1`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "bezier",
        vector1: {
            distance: 75,
            angle: 0
        },
        vector2: {
            distance: 75,
            angle: 180
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.vector1`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 900,
            y: 160
        },
        vector1: {
            angle: 20,
            distance: 75
        },
        vector2: {
            angle: 20,
            distance: 75
        }
    }],
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the length and angle between the second control point and end point of bezier segment
</b></td>
<td>
<b>Property</b>:<i>`connectors.segments.vector2`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    segments: [{
        type: "bezier",
        vector1: {
            distance: 75,
            angle: 0
        },
        vector2: {
            distance: 75,
            angle: 180
        }
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.segments.vector2`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 900,
            y: 160
        },
        vector1: {
            angle: 20,
            distance: 75
        },
        vector2: {
            angle: 20,
            distance: 75
        }
    }]
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the type of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.shape.type`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    shape: {
        type: "bpmn"
    },
    segments: [{
        type: "straight"
    }]
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.shape.type`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    segments: [{
        type: 'Bezier',
        point: {
            x: 600,
            y: 300
        },
        point1: {
            x: 525,
            y: 475
        },
        point2: {
            x: 575,
            y: 475
        }
    }],
    shape: {
        type: 'Bpmn',
        flow: 'Message',
        message: 'InitiatingMessage'
    }
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the source decorator of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border color of the source decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.borderColor`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow",
        borderColor: "red"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.style.strokeColor`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
        style: {
            strokeColor: 'red'
        },
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Sets the border width of the decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.borderWidth`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow",
        borderWidth: 5
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.style.strokeWidth`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
        strokeWidth: 5
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines to customize sourceDecorator appearance using user-defined CSS
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.cssClass`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow",
        cssClass: "hoverDecorator"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the fill color of the source decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.fillColor`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow",
        fillColor: "red"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.style.fill`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
        fill: 'black'
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Sets the height of the source decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.height`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        width: 10,
        height: 10
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.height`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
        height: 10,
        width: 10
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the custom shape of the source decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.pathData`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "path",
        pathData: "M 376.892, 225.284 L 371.279,211.95 L 376.892,198.617 L 350.225,211.95 L 376.892,225.284 Z"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.pathData`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Custom',
        pathData: "M 376.892,225.284 L 371.279,211.95 L 376.892,198.617 L 350.225,211.95 L 376.892,225.284 Z"
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the shape of the source decorator.
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.shape`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: ej.datavisualization.Diagram.DecoratorShapes.Circle
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.shape`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the width of the source decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceDecorator.width`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    sourceDecorator: {
        shape: "openarrow",
        width: 10,
        height: 10
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceDecorator.width`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    sourceDecorator: {
        shape: 'Arrow',
        width: 10,
        height: 10
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Sets the source node of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourceNode`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50
};
var node2 = {
    name: "target",
    offsetX: 300,
    offsetY: 300,
    width: 50,
    height: 50
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector], nodes:[ node1, node2 ]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourceID`</i>
</br>
</br>
<code>
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90
    }
];
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourceID: 'source',
    targetID: 'target'
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the space to be left between the source node and the source point of a connector</b></td>
<td>
<b>Property</b>:<i>`connectors.sourcePadding`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50
};
var node2 = {
    name: "target",
    offsetX: 300,
    offsetY: 300,
    width: 50,
    height: 50
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target",
    sourcePadding: 2,
    targetPadding: 2
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [node1, node2]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.hitPadding`</i>
</br>
</br>
<code>
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90
    }
];
var connectors = [{
    id: 'connector',
    type: 'Straight',
    hitPadding: 2
    sourceID: 'source',
    targetID: 'target'
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the start point of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourcePoint`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourcePoint`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the source port of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.sourcePort`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50,
    ports: [{
        name: "port",
        offset: {
            x: 1,
            y: 0.5
        }
    }]
};
var node2 = {
    name: "target",
    offsetX: 200,
    offsetY: 200,
    width: 50,
    height: 50,
    ports: [{
        name: "port1",
        offset: {
            x: 0,
            y: 0.5
        }
    }]
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target",
    sourcePort: "port",
    targetPort: "port1"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [node1, node2]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.sourcePortID`</i>
</br>
</br>
<code>

var nodeport1 = {
    id: 'port',
    shape: 'Square',
    offset: {
        x: 1,
        y: 0.5
    }
};
var nodeport2 = {
    id: 'port1',
    shape: 'Square',
    offset: {
        x: 0,
        y: 0.5
    }
};
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90,
        ports: [nodeport1]
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90,
        ports: [nodeport2]
    }
];

var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourceID: 'source',
    targetID: 'target',
    sourcePortID: 'port',
    targetPortID: 'port1',
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the target decorator of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border color of the target decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.borderColor`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow",
        borderColor: "red"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.style.strokeColor`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
        style: {
            strokeColor: 'red'
        },
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Sets the border width of the decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.borderWidth`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow",
        borderWidth: 5
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.style.strokeWidth`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
        strokeWidth: 5
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines to customize target Decorator appearance using user-defined CSS
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.cssClass`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow",
        cssClass: "hoverDecorator"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the fill color of the target decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.fillColor`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow",
        fillColor: "red"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.style.fill`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
        fill: 'black'
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Sets the height of the target decorator</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.height`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        width: 10,
        height: 10
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.height`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
        height: 10,
        width: 10
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the custom shape of the target decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.pathData`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "path",
        pathData: "M 376.892,225.284 L 371.279,211.95 L 376.892,198.617 L 350.225,211.95 L 376.892,225.284 Z"
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.pathData`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Custom',
        pathData: "M 376.892,225.284 L 371.279,211.95 L 376.892,198.617 L 350.225,211.95 L 376.892,225.284 Z"
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the shape of the target decorator.
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.shape`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: ej.datavisualization.Diagram.DecoratorShapes.Circle
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.shape`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the width of the target decorator
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetDecorator.width`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    targetDecorator: {
        shape: "openarrow",
        width: 10,
        height: 10
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetDecorator.width`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 500,
        y: 100
    },
    targetPoint: {
        x: 600,
        y: 200
    },
    targetDecorator: {
        shape: 'Arrow',
        width: 10,
        height: 10
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the target node of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetNode`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50
};
var node2 = {
    name: "target",
    offsetX: 300,
    offsetY: 300,
    width: 50,
    height: 50
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [node1, node2]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetID`</i>
</br>
</br>
<code>
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90
    }
];
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourceID: 'source',
    targetID: 'target'
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the space to be left between the target node and the target point of a connector</b></td>
<td>
<b>Property</b>:<i>`connectors.targetPadding`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50
};
var node2 = {
    name: "target",
    offsetX: 300,
    offsetY: 300,
    width: 50,
    height: 50
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target",
    sourcePadding: 2,
    targetPadding: 2
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [node1, node2]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.hitPadding`</i>
</br>
</br>
<code>
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90
    }
];
var connectors = [{
    id: 'connector',
    type: 'Straight',
    hitPadding: 2
    sourceID: 'source',
    targetID: 'target'
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the start point of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetPoint`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    }
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetPoint`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the target port of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.targetPort`</i>
</br>
</br>
<code>
var node1 = {
    name: "source",
    offsetX: 100,
    offsetY: 100,
    width: 50,
    height: 50,
    ports: [{
        name: "port",
        offset: {
            x: 1,
            y: 0.5
        }
    }]
};
var node2 = {
    name: "target",
    offsetX: 200,
    offsetY: 200,
    width: 50,
    height: 50,
    ports: [{
        name: "port1",
        offset: {
            x: 0,
            y: 0.5
        }
    }]
};
var connector = {
    name: "connector",
    sourceNode: "source",
    targetNode: "target",
    sourcePort: "port",
    targetPort: "port1"
};
$("#diagramcontent").ejDiagram({
    connectors: [connector],
    nodes: [node1, node2]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.targetPortID`</i>
</br>
</br>
<code>

var nodeport1 = {
    id: 'port',
    shape: 'Square',
    offset: {
        x: 1,
        y: 0.5
    }
};
var nodeport2 = {
    id: 'port1',
    shape: 'Square',
    offset: {
        x: 0,
        y: 0.5
    }
};
var nodes = [{
        id: 'source',
        width: 60,
        height: 60,
        offsetX: 75,
        offsetY: 90,
        ports: [nodeport1]
    },
    {
        id: 'target',
        width: 75,
        height: 70,
        offsetX: 210,
        offsetY: 90,
        ports: [nodeport2]
    }
];

var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourceID: 'source',
    targetID: 'target',
    sourcePortID: 'port',
    targetPortID: 'port1',
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors,
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the tooltip that should be shown when the mouse hovers over connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.tooltip`</i>
</br>
</br>
<code>
<script type="text/x-jsrender" id="mouseovertooltip">
   <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;">  </span>
   </div>
</script>
var tooltip = {
    templateId: "mouseovertooltip",
    alignment: {
        horizontal: "center",
        vertical: "bottom"
    }
};
var ConnectorConstraints = ej.datavisualization.Diagram.ConnectorConstraints;
var connector = {
    name: "flow",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.InheritTooltip,
    tooltip: tooltip
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
}) < script type = "text/x-jsrender"
id = "mouseovertooltip" >
    <
    div style = "background-color: #F08080; color: white; white-space: nowrap; height: 20px" >
    <
    span style = "padding: 5px;" > < /span> <
    /div> <
    /script>
var tooltip = {
    templateId: "mouseovertooltip",
    alignment: {
        horizontal: "center",
        vertical: "bottom"
    }
};
var ConnectorConstraints = ej.datavisualization.Diagram.ConnectorConstraints;
var connector = {
    name: "flow",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default & ~ConnectorConstraints.InheritTooltip,
    tooltip: tooltip
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});;
</code>
</td><td>
<b>Property</b>:<i>`connectors.tooltip`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    constraints: ConnectorConstraints.Default | ConnectorConstraints.Tooltip,
    tooltip: {
        content: 'Connector',
        position: 'TopCenter',
        showTipPointer: true,
    },
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the vertical alignment of connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.verticalAlign`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 150,
        y: 150
    },
    verticalAlign: ej.datavisualization.Diagram.VerticalAlignment.Bottom
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Enables or disables the visibility of connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.visible`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    visible: true
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.visible`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    visible: true
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the z-index of the connector
</b></td>
<td>
<b>Property</b>:<i>`connectors.zOrder`</i>
</br>
</br>
<code>
var connector = {
    name: "connector",
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    zOrder: 1000
};
$("#diagramcontent").ejDiagram({
    connectors: [connector]
});
</code>
</td><td>
<b>Property</b>:<i>`connectors.zIndex`</i>
</br>
</br>
<code>
var connectors = [{
    id: 'connector',
    type: 'Straight',
    sourcePoint: {
        x: 100,
        y: 100
    },
    targetPoint: {
        x: 200,
        y: 200
    },
    zIndex: -1
}];
var diagram = new ej.diagrams.Diagram({
    connectors: connectors
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Binds the custom JSON data with connector properties
</b></td>
<td>
<b>Property</b>:<i>`connectors.connectorTemplate`</i>
</br>
</br>
<code>
 var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: "Id",
        parent: "ReportingPerson",
        dataSource: data
    },
    connectorTemplate: "connectorTemplate"
});

function connectorTemplate(diagram, connector) {
    if (connector.sourceNode && connector.targetNode) {
        connector.linecolor = "green";
    }
}
</code>
</td><td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Enables/Disables the default behaviors of the diagram
</b></td>
<td>
<b>Property</b>:<i>`constraints`</i>
</br>
</br>
<code>
var DiagramConstraints = ej.datavisualization.Diagram.DiagramConstraints;
$("#diagramcontent").ejDiagram({
    constraints: DiagramConstraints.Default | DiagramConstraints.Bridging
});
</code>
</td><td>
<b>Property</b>:<i>`constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    constraints: DiagramConstraints.Default | DiagramConstraints.Bridging
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## ContextMenu

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the collection of context menu items</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items`</i>
</br>
</br>
<code>
var menuitems = [{
    "name": "hyperLink",
    "text": "Hyperlink",
    "image": "",
    "style": ""
}];
var contextMenu = {
    items: menuitems
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'delete',
            id: 'delete',
            target: '.e-diagramcontent',
            iconCss: 'e-copy'
        }],
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the text for the collection of context menu item</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items.text`</i>
</br>
</br>
<code>
var menuitems = [{
    "text": "ZoomIn"
}];
var contextMenu = {
    items: menuitems
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.text`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'ZoomIn'
        }],
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the name for the collection of context menu items</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items.name`</i>
</br>
</br>
<code>
var menuitems = [{
    "name": "hyperLink"
}];
var contextMenu = {
    items: menuitems
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.id`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'delete',
            id: 'delete'
        }]
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the image url for the collection of context menu items</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items.imageUrl`</i>
</br>
</br>
<code>
var menuitems = [{
    "name": "zoomin",
    "text": "ZoomIn",
    "imageUrl": "Images/zoomin.png",
    "style": ""
}];
var contextMenu = {
    items: menuitems
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.url`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
            contextMenuSettings: {
                show: true,
                items: [{
                    'id': 'zoomin',
                    'text': 'ZoomIn',
                    'url': 'Images/zoomin.png',
                }],
            },
        });
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the cssClass for the collection of context menu items</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items.cssClass`</i>
</br>
</br>
<code>
var menuitems = [{
    "name": "zoomin",
    "text": "ZoomIn",
    "imageUrl": "Images/zoomin.png",
    "cssClass": "menu",
    "style": ""
}];
var contextMenu = {
    items: menuitems
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.iconCss`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'delete',
            id: 'delete',
            target: '.e-diagramcontent',
            iconCss: 'e-copy'
        }],
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Defines the collection of sub items for the context menu items</b></td>
<td>
<b>Property</b>:<i>`contextMenu.items.subItems`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    contextMenu: {
        items: [{
            name: "zoom",
            text: "Zoom",
            subItems: [{
                name: "zoomIn",
                text: "ZoomIn"
            }, {
                name: "zoomOut",
                text: "ZoomOut"
            }]
        }]
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'Zoom',
            id: 'zoom',
            items: [{
                name: "zoomIn",
                text: "ZoomIn"
            }, {
                name: "zoomOut",
                text: "ZoomOut"
            }]
        }],
        showCustomMenuOnly: false,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
<tr>
<td><b>Set whether to display the default context menu items or not</b></td>
<td>
<b>Property</b>:<i>`contextMenu.showCustomMenuItemsOnly`</i>
</br>
</br>
<code>
var contextMenu = {
    showCustomMenuItemsOnly: true
};
$("#diagramcontent").ejDiagram({
    contextMenu: contextMenu
});
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.showCustomMenuOnly`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        showCustomMenuOnly: false,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Specifies separator between the menu items</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.separator`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
            contextMenuSettings: {
                show: true,
                items: [{
                        text: 'Save',
                        id: 'save',
                        target: '.e-diagramcontent',
                        iconCss: 'e-save',
                        separator: true
                    },
                    {
                        text: 'Load',
                        id: 'load',
                        target: '.e-diagramcontent',
                        iconCss: 'e-load'
                    },
                },
            });
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Define the target to show the menu item.</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.items.target`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'delete',
            id: 'delete',
            target: '.e-diagramcontent',
            iconCss: 'e-copy'
        }],
        showCustomMenuOnly: false,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables/Disables the context menu items</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.show`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true,
        items: [{
            text: 'delete',
            id: 'delete',
            target: '.e-diagramcontent',
            iconCss: 'e-copy'
        }],
        showCustomMenuOnly: false,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## DataSourceSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the data source either as a collection of objects or as an instance of ej.DataManager</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.dataSource`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];

$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        dataSource: data
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`dataSourceSettings.dataManager`</i>
</br>
</br>
<code>
var items = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
var diagram = new ej.diagrams.Diagram({
    dataSourceSettings: {
        dataManager: items
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the unique id of the data source items</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.id`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];

$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: "Id",
        dataSource: data
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`dataSourceSettings.id`</i>
</br>
</br>
<code>
var items = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
var diagram = new ej.diagrams.Diagram({
    dataSourceSettings: {
        id: 'Id',
        dataManager: items
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the parent id of the data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.parent`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];

$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: "Id",
        parent: "ReportingPerson",
        dataSource: data
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`dataSourceSettings.parentId`</i>
</br>
</br>
<code>
var items = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
var diagram = new ej.diagrams.Diagram({
    dataSourceSettings: {
        id: 'Id',
        parentId: 'ReportingPerson',
        dataManager: items
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes query to retrieve a set of data from the specified datasource</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.query`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        dataSource: ej.DataManager({
            url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
        }),
        query: ej.Query().from("Employees").select("EmployeeID,ReportsTo,FirstName"),
        tableName: "Employees",
        id: "EmployeeID",
        parent: "ReportsTo"
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the unique id of the root data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.root`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];

$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: "Id",
        parent: "ReportingPerson",
        root: "E1",
        dataSource: data
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`dataSourceSettings.root`</i>
</br>
</br>
<code>
var items = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
var diagram = new ej.diagrams.Diagram({
    dataSourceSettings: {
        id: 'Id',
        parentId: 'ReportingPerson',
        dataManager: items,
        root: 'E1'
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the name of the table on which the specified query has to be executed</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.tableName`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        dataSource: ej.DataManager({
            url: "http://mvc.syncfusion.com/Services/Northwnd.svc/"
        }),
        query: ej.Query().from("Employees").select("EmployeeID,ReportsTo,FirstName"),
        //Table name
        tableName: "Employees",
        id: "EmployeeID",
        parent: "ReportsTo"
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the method name which is used to get the updated data from client side to the server side
</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.crudAction`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    crudAction:
                    {
                        read: http://js.syncfusion.com/demos/ejservices/api/Diagram/GetNodes
                        }
                }
   });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the create method which is used to get the nodes to be added from client side to the server side
</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.crudAction.create`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    crudAction:
                    {
                        create: "http://js.syncfusion.com/demos/ejservices/api/Diagram/AddNodes",
                        }
                }
   });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Specifies the update method which is used to get the updated data from client side to the server side
</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.crudAction.update`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    crudAction:
                    {
                        update: "http://js.syncfusion.com/demos/ejservices/api/Diagram/UpdateNodes",
                        }
                }
   });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Specifies the destroy method which is used to get the deleted items data from client side to the server side
</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.crudAction.destroy`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    crudAction:
                    {
                        destroy: "http://js.syncfusion.com/demos/ejservices/api/Diagram/DeleteNodes"
                        }
                }
   });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Specifies the read method to get the created nodes from client side to the server side
</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.crudAction.read`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    crudAction:
                    {
                        read: http://js.syncfusion.com/demos/ejservices/api/Diagram/GetNodes
                        }
                }
   });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the data source either as a collection of objects or as an instance of ej.DataManager</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.customFields`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: 'Name',
        customFields: [
            "Description",
            "Color"
            ]
        }
   });
</code>
</td>
<td>
<b>Property</b>:<i>`dataSourceSettings.data`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    dataSourceSettings: { id: 'Name',
        customFields: [
            "Description",
            "Color"
            ] },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the data source either as a collection of objects or as an instance of ej.DataManager</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name"
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the datasource for the connection datasource settings items</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.dataSource`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];
$("#diagramcontent").ejDiagram({
dataSourceSettings: {
    id: "Name",
    connectionDataSource: {
        id: "Name",
        dataSource: data
    }
}
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the unique id of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.id`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name"
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the source node of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.sourceNode`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        sourceNode: "sourceNode",
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the target node of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.targetNode`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        targetNode: "targetNode"
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the sourcePointX value of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.sourcePointX`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        sourcePointX:200
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the sourcePointY value of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.sourcePointY`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        sourcePointY:200
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the targetPoint-x value of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.targetPointX`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        targetPointX:200
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the targetPoint-y value of the connection data source item</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.targetPointY`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        targetPointY:200
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Specifies the method name which is used to get updated connectors from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.crudAction`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        sourceNode: "sourceNode",
                        targetNode: "targetNode",
                        crudAction: {
                        read: http://js.syncfusion.com/demos/ejservices/api/Diagram/GetConnectors"
                        }
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the create method which is used to get the connectors to be added from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.crudAction.create`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        sourceNode: "sourceNode",
                        targetNode: "targetNode",
                        crudAction: {
                        create: http://js.syncfusion.com/demos/ejservices/api/Diagram/AddConnectors",
                        }
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the update method which is used to get the updated connectors from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.crudAction.update`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        crudAction: {
                         update: http://js.syncfusion.com/demos/ejservices/api/Diagram/UpdateConnectors",
                        }
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the destroy method which is used to get the deleted items data from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.crudAction.destroy`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        crudAction: {
                        destroy: http://js.syncfusion.com/demos/ejservices/api/Diagram/DeleteConnectors"
                        }
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the read method which is used to get the data from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.crudAction.read`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        crudAction: {
                        read: http://js.syncfusion.com/demos/ejservices/api/Diagram/GetConnectors"
                        }
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Specifies the custom fields to get the updated data from client side to the server side</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.connectionDataSource.customFields`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    dataSourceSettings:
                {
                    id: "Name",
                    connectionDataSource:
                    {
                        id: "Name",
                        customFields: [ "Description", "Color"]
                    }
                }
            });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Binds the custom data with node model</b></td>
<td>
<b>Property</b>:<i>`dataSourceSettings.doBinding`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    width: 1500, height: 2500,
    layout: { type: 'HierarchicalTree', verticalSpacing: 40 },
    dataSourceSettings: {
        id: 'Name', parentId: 'ReportingPerson', dataManager: items,
        doBinding: (nodeModel: NodeModel, data: object, diagram: Diagram) => {
            nodeModel.annotations = [{
                content: data['Name'], margin: { top: 10 }
            }];
        }
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
</table>

## DefaultSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Initializes the default values for nodes and connectors</b></td>
<td>
<b>Property</b>:<i>`defaultSettings.node`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    defaultSettings: { node: { fillColor:"red"} }
   });
</code>
</td>
<td>
<b>Property</b>:<i>`getNodeDefaults`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
     getNodeDefaults: (object: Node) => {
        object.style = { fill: 'lightgrey', strokeColor: 'none', strokeWidth: 2 };
        return object;
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Initializes the default connector properties</b></td>
<td>
<b>Property</b>:<i>`defaultSettings.connector`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    defaultSettings: { connector: { lineColor:"red", lineWidth:4, lineDashArray:"2,2" } }
   });
</code>
</td>
<td>
<b>Property</b>:<i>`getConnectorDefaults`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
     getConnectorDefaults: (connector: ConnectorModel) => {
        connector= {
            targetDecorator:{shape  'None'},
            type : 'Orthogonal'};
        return connector;
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Initializes the default properties of groups</b></td>
<td>
<b>Property</b>:<i>`defaultSettings.group`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    defaultSettings: { group: {constraints: ej.datavisualization.Diagram.NodeConstraints.Default & ~ej.datavisualization.Diagram.NodeConstraints.Drag } }
   });
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>
</table>

## DrawType

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Sets the type of JSON object to be drawn through drawing tool</b></td>
<td>
<b>Property</b>:<i>`drawType`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    drawType:{type:"node"}
   });
</code>
</td>
<td>
<b>Property</b>:<i>`drawingObject`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    drawingObject : {id: 'connector', type: 'Straight'}
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## EnableAutoScroll

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Enables or disables auto scroll in diagram</b></td>
<td>
<b>Property</b>:<i>`enableAutoScroll`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    enableAutoScroll: false
   });
</code>
</td>
<td>
<b>Property</b>:<i>`canAutoScroll`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    canAutoScroll: true
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## EnableContextMenu

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Enables or disables diagram context menu</b></td>
<td>
<b>Property</b>:<i>`enableContextMenu`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    enableContextMenu: false
   });
</code>
</td>
<td>
<b>Property</b>:<i>`contextMenuSettings.show`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    contextMenuSettings: {
        show: true
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## GetCustomCursor

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Enable or disable rendering component with custom cursor<b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`getCustomCursor`</i>
</br>
</br>
<code>
function getCustomCursor(action: string, active: boolean): string {
var cursor;
if (active && action === 'Drag') {
cursor = '-webkit-grabbing';
} else if (action === 'Drag') {
cursor = '-webkit-grabbing'
}
return cursor;
}
var nodes = [{
          id: 'node1', width: 100, height: 100, offsetX: 100, offsetY: 100,
      },
      {
          id: 'node2', width: 100, height: 100, offsetX: 300, offsetY: 100,
          shape: { type: 'Basic', shape: 'Ellipse' },
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes,
    getCustomCursor: getCustomCursor
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## GetCustomProperty

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allows to get the custom properties that have to be serialized<b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`getCustomProperty`</i>
</br>
</br>
<code>
var nodes = [{
          id: 'node1', width: 100, height: 100, offsetX: 100, offsetY: 100,
      },
      {
          id: 'node2', width: 100, height: 100, offsetX: 300, offsetY: 100,
          shape: { type: 'Basic', shape: 'Ellipse' },
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes,
    getCustomProperty: (key: string) => {
        if (key === 'nodes') {
            return ['description'];
            }
        return null;
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## GetDescription

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allows to get the custom description<b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`getDescription`</i>
</br>
</br>
<code>
function getAccessibility(object: ConnectorModel, diagram: Diagram): string {
    var value;
    if (object instanceof Connector) {
        value = 'clicked on Connector';
    } else {
        value = undefined;
    }
    return value;
}
var nodes = [{
          id: 'node1', width: 100, height: 100, offsetX: 100, offsetY: 100,
      },
      {
          id: 'node2', width: 100, height: 100, offsetX: 300, offsetY: 100,
          shape: { type: 'Basic', shape: 'Ellipse' },
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes,
    getDescription: getAccessibility
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## GetCustomTool

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allows to get the custom tool<b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`getCustomTool`</i>
</br>
</br>
<code>
function getTool(action: string): ToolBase {
    var tool;
    if (action === 'userHandle') {
        tool = new CloneTool(diagram.commandHandler, true);
    }
    return tool;
}
class CloneTool extends ToolBase {
    public mouseDown(args: MouseEventArgs): void {
        super.mouseDown(args);
        diagram.copy();
        diagram.paste();
    }
}
var nodes = [{
          id: 'node1', width: 100, height: 100, offsetX: 100, offsetY: 100,
      },
      {
          id: 'node2', width: 100, height: 100, offsetX: 300, offsetY: 100,
          shape: { type: 'Basic', shape: 'Ellipse' },
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes,
    getCustomTool: getTool
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## Height

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Specifies the height of the diagram</b></td>
<td>
<b>Property</b>:<i>`height`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    height:"500",
    width:"500"
   });
</code>
</td>
<td>
<b>Property</b>:<i>`height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    height: 1000
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## HistoryManager

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>A method that takes a history entry as argument and returns whether the specific entry can be popped or not</b></td>
<td>
<b>Property</b>:<i>`historyManager.canPop`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
var entry = { object: node, prevState: node.empInfo };
diagram.model.historyManager.push(entry);
var value = { role: "New role" };
node.empInfo = value;

if(diagram.model.historyManager.canPop(entry)){
    diagram.model.historyManager.pop();
}
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A method that ends grouping the changes</b></td>
<td>
<b>Property</b>:<i>`historyManager.closeGroupAction`</i>
</br>
</br>
<code>
var group = diagram.model.selectedItems;
diagram.model.historyManager.startGroupAction();

for (var i = 0; i < group.children.length; i++) {
    var option = {};
    var item = group.children[i];
    // Updates the fillColor for all the child elements.
    option.fillColor = args.style.backgroundColor;
    diagram.updateNode(item.name, option);
}

diagram.model.historyManager.closeGroupAction();
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.endGroupAction`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node1',
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    },
    {
        offsetX: 200,
        offsetY: 200,
        width: 100,
        height: 100,
        id: 'node2'
    }],
    connectors: [{
        id: 'connector1', sourcePoint: { x: 100, y: 200 },
        targetPoint: { x: 200, y: 300 },
        type: 'Orthogonal'
        }]
});
diagram.appendTo('#diagram');
var objects = [];
            objects.push(diagram.nodes[0], diagram.nodes[1], diagram.connectors[0]);
            diagram.historyList.startGroupAction();
            diagram.distribute('Top', objects);
            diagram.distribute('Bottom', objects);
            diagram.distribute('BottomToTop', objects);
            diagram.historyList.endGroupAction();
</code></td>
</tr>

<tr>
<td><b>A method that removes the history of a recent change made in diagram</b></td>
<td>
<b>Property</b>:<i>`historyManager.pop`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.model.historyManager.pop();
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A method that allows to track the custom changes made in diagram</b></td>
<td>
<b>Property</b>:<i>`historyManager.push`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");

var entry = { object: node, prevState: node.empInfo };
diagram.model.historyManager.push(entry);

var value = { role: "New role" };
node.empInfo = value;
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.push`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
var object = diagram.nodes[0];
    object['description'] = (document.getElementById('custom') as HTMLSelectElement).value;
    var entry = { undoObject: object };
    diagram.historyList.push(entry);
    diagram.dataBind();
</code></td>
</tr>

<tr>
<td><b>Defines what should be happened while trying to restore a custom change</b></td>
<td>
<b>Property</b>:<i>`historyManager.redo`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    historyManager: {
        undo: customUndoRedo,
        redo: customUndoRedo
    }
});

function customUndoRedo(args) {
    var diagram = $("#diagramcontent").ejDiagram("instance");
    var node = args.object;
    var currentState = node.empInfo;

    node.empInfo = args.prevState;

    args.prevState = currentState;
}
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.redo`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
var node1 = diagram.nodes[0];
node1['customName'] = 'customNode';
entry = {
    undoObject: node1
};
diagram.historyList.push(entry);
diagram.historyList.undo = function(args: HistoryEntry) {
    args.redoObject = cloneObject(args.undoObject) as NodeModel;
    args.undoObject['customName'] = 'customNodeChange';
}
diagram.historyList.redo = function(args: HistoryEntry) {
    var current = cloneObject(args.undoObject) as NodeModel;
    args.undoObject['customName'] = args.redoObject['customName'];
    args.redoObject = current;
}
</code></td>
</tr>

<tr>
<td><b>Gets the number of redo actions to be stored on the history manager. Its an read-only property and the collection should not be modified</b></td>
<td>
<b>Property</b>:<i>`historyManager.redoStack`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.model.historyManager.redoStack();
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.redoStack`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.redoStack();
</code></td>
</tr>

<tr>
<td><b>Restricts the undo and redo actions to a certain limit</b></td>
<td>
<b>Property</b>:<i>`historyManager.stackLimit`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.model.historyManager.stackLimit();
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A method that starts to group the changes to revert/restore them in a single undo or redo</b></td>
<td>
<b>Property</b>:<i>`historyManager.startGroupAction`</i>
</br>
</br>
<code>
var group = diagram.model.selectedItems

diagram.model.historyManager.startGroupAction();

for (var i = 0; i < group.children.length; i++) {
    var option = {};
    var item = group.children[i];
    option.fillColor = args.style.backgroundColor;
    diagram.updateNode(item.name, option);
}

diagram.model.historyManager.closeGroupAction();
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.startGroupAction`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node1',
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    },
    {
        offsetX: 200,
        offsetY: 200,
        width: 100,
        height: 100,
        id: 'node2'
    }],
    connectors: [{
        id: 'connector1', sourcePoint: { x: 100, y: 200 }, targetPoint: { x: 200, y: 300 },
        type: 'Orthogonal'
        }]
});
diagram.appendTo('#diagram');
var objects = [];
            objects.push(diagram.nodes[0], diagram.nodes[1], diagram.connectors[0]);
            diagram.historyList.startGroupAction();
            diagram.distribute('Top', objects);
            diagram.distribute('Bottom', objects);
            diagram.distribute('BottomToTop', objects);
            diagram.historyList.endGroupAction();
</code></td>
</tr>

<tr>
<td><b>Defines what should be happened while trying to revert a custom change</b></td>
<td>
<b>Property</b>:<i>`historyManager.undo`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    historyManager: {
        undo: customUndoRedo,
        redo: customUndoRedo
    }
});

function customUndoRedo(args) {
    var diagram = $("#diagramcontent").ejDiagram("instance");
    var node = args.object;
    var currentState = node.empInfo;

    node.empInfo = args.prevState;

    args.prevState = currentState;
}
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.undo`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
var node1 = diagram.nodes[0];
node1['customName'] = 'customNode';
entry = {
    undoObject: node1
};
diagram.historyList.push(entry);
diagram.historyList.undo = function(args: HistoryEntry) {
    args.redoObject = cloneObject(args.undoObject) as NodeModel;
    args.undoObject['customName'] = 'customNodeChange';
}
diagram.historyList.redo = function(args: HistoryEntry) {
    var current = cloneObject(args.undoObject) as NodeModel;
    args.undoObject['customName'] = args.redoObject['customName'];
    args.redoObject = current;
}
</code></td>
</tr>

<tr>
<td><b>Gets the number of undo actions to be stored on the history manager. Its an read-only property and the collection should not be modified</b></td>
<td>
<b>Property</b>:<i>`historyManager.undoStack`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.model.historyManager.undoStack();
</code>
</td>
<td>
<b>Property</b>:<i>`historyList.undoStack`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.undoStack();
</code></td>
</tr>

<tr>
<td><b>Set the current entry object</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`historyList.currentEntry`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.currentEntry();
</code></td>
</tr>

<tr>
<td><b>Set the history entry can be undo</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`historyList.canUndo`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.canUndo = true;
</code></td>
</tr>
<tr>
<td><b>Set the history entry can be redo</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`historyList.canRedo`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.canRedo = true;
</code></td>
</tr>
<tr>
<td><b>Used to decide to stored the changes to history</b></td>
<td>
<b>Property</b>:<i>`historyManager.canLog`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.model.historyManager.canLog();
</code>
</td></td>
<td>
<b>Property</b>:<i>`historyList.canLog`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
diagram.historyList.canLog = function (entry: HistoryEntry) {
        entry.cancel = true;
        return entry;
    }
</code></td>
</tr>
</table>

## LabelRenderingMode

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>
<tr>
<td><b>Defines the type of the rendering mode of label</b></td>
<td>
<b>Property</b>:<i>`labelRenderingMode`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({ labelRenderingMode: "svg" });
</code></td>
<td>
<b>Not applicable</b></td>
</tr>
</table>

## Layout

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Specifies the custom bounds to arrange/align the layout</b></td>
<td>
<b>Property</b>:<i>`layout.bounds`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { bounds:{ x: 0, y: 0, width: 1000, height: 1000} }});
</code>
</td>
<td>
<b>Property</b>:<i>`layout.bounds`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        bounds: new Rect(0, 0, 500, 500)
}
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the fixed node with reference to which, the layout will be arranged and fixed node will not be repositioned</b></td>
<td>
<b>Property</b>:<i>`layout.fixedNode`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    fixedNode: "node" });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.fixedNode`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        fixedNode: 'node'
}
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Customizes the orientation of trees/sub trees</b></td>
<td>
<b>Property</b>:<i>`layout.getLayoutInfo`</i>
</br>
</br>
<code>
function getLayoutInfo(diagram, node, options) { options.orientation = "vertical"; options.type = "left"; offset = 10;};

$("#diagramcontent").ejDiagram({
    layout: { getLayoutInfo:getLayoutInfo }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.getLayoutInfo`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        getLayoutInfo: (node: Node, tree: TreeInfo) => {
            if (!tree.hasSubTree) {
                tree.orientation = 'vertical';
            }
        }
}
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines a method to customize the segments based on source and target nodes</b></td>
<td>
<b>Property</b>:<i>`layout.getConnectorSegments`</i>
</br>
</br>
<code>
function getConnectorSegment(diagram, node, options) { };
$("#diagramcontent").ejDiagram({layout: { getConnectorSegments:getConnectorSegment } });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.connectorSegments`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        connectorSegments: 'Default'
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the space to be horizontally left between nodes</b></td>
<td>
<b>Property</b>:<i>`layout.horizontalSpacing`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({layout: { horizontalSpacing: 50 }});
</code>
</td>
<td>
<b>Property</b>:<i>`layout.horizontalSpacing`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        horizontalSpacing: 30
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the space to be left between layout bounds and layout</b></td>
<td>
<b>Property</b>:<i>`layout.margin`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { margin:{ left: 10, right: 10, top: 10, bottom: 10} }});
</code>
</td>
<td>
<b>Property</b>:<i>`layout.margin`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    layout: {
        margin: { left: 50, top: 50, right: 0, bottom: 0 }
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how to horizontally align the layout within the layout bounds</b></td>
<td>
<b>Property</b>:<i>`layout.horizontalAlignment`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { horizontalAlignment:ej.datavisualization.Diagram.HorizontalAlignment.Center }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.horizontalAlignment`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        horizontalAlignment: 'Center'
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how to vertically align the layout within the layout bounds</b></td>
<td>
<b>Property</b>:<i>`layout.verticalAlignment`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: {
        verticalAlignment:ej.datavisualization.Diagram.VerticalAlignment.Center
        }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.verticalAlignment`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        verticalAlignment: 'Center'
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the orientation/direction to arrange the diagram elements</b></td>
<td>
<b>Property</b>:<i>`layout.orientation`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { orientation: ej.datavisualization.Diagram.LayoutOrientations.LeftToRight }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.orientation`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        orientation: 'TopToBottom',}
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the type of the layout based on which the elements will be arranged</b></td>
<td>
<b>Property</b>:<i>`layout.type`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({ layout: {
    type: ej.datavisualization.Diagram.LayoutTypes.HierarchicalTree }
s});
</code>
</td>
<td>
<b>Property</b>:<i>`layout.type`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        type: 'OrganizationalChart'
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the space to be vertically left between nodes</b></td>
<td>
<b>Property</b>:<i>`layout.verticalSpacing`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { verticalSpacing: 50 }});
</code>
</td>
<td>
<b>Property</b>:<i>`layout.verticalSpacing`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        verticalSpacing: 30
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the value is used to define the root node of the layout</b></td>
<td>
<b>Property</b>:<i>`layout.root`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { root: 'rootNode' }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.root`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        root: 'rootNode'
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how long edges should be, ideally. This will be the resting length for the springs</b></td>
<td>
<b>Property</b>:<i>`layout.springFactor`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { springFactor: 0.442 }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.springFactor`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        type: 'SymmetricalLayout', springLength: 80, springFactor: 0.8,
        maxIteration: 500,
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how long edges should be, ideally. This will be the resting length for the springs</b></td>
<td>
<b>Property</b>:<i>`layout.maxIteration`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { maxIteration: 442 }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.maxIteration`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        type: 'SymmetricalLayout', springLength: 80, springFactor: 0.8,
        maxIteration: 500,
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how long edges should be, ideally. This will be the resting length for the springs</b></td>
<td>
<b>Property</b>:<i>`layout.springLength`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    layout: { springLength: 80 }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`layout.springLength`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        type: 'SymmetricalLayout', springLength: 80, springFactor: 0.8,
        maxIteration: 500,
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets how to define the connection direction (first segment direction & last segment direction)</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`layout.connectionDirection`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        connectionDirection:'Auto',
        type: 'SymmetricalLayout', springLength: 80, springFactor: 0.8,
        maxIteration: 500,
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables/Disables animation option when a node is expanded/collapsed</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`layout.enableAnimation`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        enableAnimation: true,
        orientation: 'TopToBottom',
        type: 'OrganizationalChart', margin: { top: 20 },
        horizontalSpacing: 30, verticalSpacing: 30,
        }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether an object should be at the left/right of the mind map. Applicable only for the direct children of the root node</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`layout.getBranch`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }],
    layout: {
        type: 'MindMap',
        }
});
diagram.appendTo('#diagram');
diagram.layout.getBranch = (node: NodeModel, nodes: NodeModel[]) => {
    return 'Left';
    }
diagram.dataBind();
</code></td>
</tr>
</table>

## Nodes

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Array of JSON objects where each object represents a node</b></td>
<td>
<b>Property</b>:<i>`nodes`</i>
</br>
</br>
<code>
var nodes = [{ name: "node1", width: 175, height: 60, offsetX:100, offsetY:100}];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the type of BPMN Activity. Applicable, if the node is a BPMN activity</b></td>
<td>
<b>Property</b>:<i>`nodes.activity`</i>
</br>
</br>
<code>
var nodes = [{
    type: "bpmn", shape: ej.datavisualization.Diagram.BPMNShapes.Activity, activity: ej.datavisualization.Diagram.BPMNActivity.SubProcess, width:50, height:50
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        activity: {
            activity: 'Task'
        },
    },
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>To maintain additional information about nodes</b></td>
<td>
<b>Property</b>:<i>`nodes.addInfo`</i>
</br>
</br>
<code>
var addInfo = { TooltipData: "Shares the information with the customer" };

var node1 = { name: "node1", addInfo: addInfo, offsetX:100, offsetY:100, width:50, height:50 };

var node2 = { type: "swimlane", name: "swimlane", addInfo: addInfo };
$("#diagramcontent").ejDiagram({nodes:[node1, node2]});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.addInfo`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    addInfo: {
        "borderColor": "black", "borderWidth": '1px'
        },
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the additional information of a process. It is not directly related to the message flows or sequence flows of the process</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50,
        angle: -45, length: 150, direction: "top"
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            angle: 45,
            length: 150,
            text: 'Left',
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the angle between the BPMN shape and the annotation</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.angle`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50,
        angle: -45
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.angle`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            angle: 45,
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the direction of the text annotation</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.direction`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50,
        angle: -45, length: 150, direction: "top"
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the height of the text annotation</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.height`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50,
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.height`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            text: 'Left',
            height: 50
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the distance between the BPMN shape and the annotation</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.length`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50,
        length: 150
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.length`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            length: 150,
            text: 'Left',
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the additional information about the flow object in a BPMN Process</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.text`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape"
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.text`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            text: 'Left',
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the width of the text annotation</b></td>
<td>
<b>Property</b>:<i>`nodes.annotation.width`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1", width: 100, height:100, offsetX:50, offsetY:50,
    type:"bpmn", shape: "activity",
    annotation: {
        text: "This is a BPMN Activity shape", width: 100, height: 50
        }
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.width`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            width: 45,
            text: 'Left',
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the id for the annotation</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.annotations.id`</i>
</br>
</br>
<code>
var node = {
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: true,
            type: 'Input'
        },
        annotations: [{
            id: 'left',
            text: 'Left',
        }]
    }
};
var diagram = new ej.diagrams.Diagram({
    nodes: [node]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether the group can be ungrouped or not</b></td>
<td>
<b>Property</b>:<i>`nodes.canUngroup`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    offsetX: 150,
    offsetY: 150,
    borderColor: "red",
    borderDashArray: "4,2"
};
var group = {
    name: "group",
    children: [node1, node2],
    canUngroup: false
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Array of JSON objects where each object represents a child node/connector</b></td>
<td>
<b>Property</b>:<i>`nodes.children`</i>
</br>
</br>
<code>
var node1 = { name: "node1", width: 50, height:50, offsetX:50, offsetY:50, borderColor: "red", borderDashArray: "4,2"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    offsetX: 150,
    offsetY: 150,
    borderColor: "red",
    borderDashArray: "4,2"
};

var group = {
    name: "group",
    children: [node1, node2]
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.children`</i>
</br>
</br>
<code>
var node1 = {
    id: 'node1',
    offsetX: 250,
    offsetY: 250,
    width: 100,
    height: 100,
};
var node2 = {
    id: 'node2',
    offsetX: 450,
    offsetY: 450,
    width: 100,
    height: 100,
};
var group = {
    id: 'group',
};
group.children = ['node1', 'node2'];
var diagram = new ej.diagrams.Diagram({
    nodes: [group]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the type of UML classifier</b></td>
<td>
<b>Property</b>:<i>`nodes.classifier`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient", offsetX: 100, offsetY: 100, borderWidth: 2, borderColor: "black",
    type: "umlclassifier", classifier: ej.datavisualization.Diagram.ClassifierShapes.Class
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the name, attributes and methods of a Class. Applicable, if the node is a Class</b></td>
<td>
<b>Property</b>:<i>`nodes.class`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the name of class</b></td>
<td>
<b>Property</b>:<i>`nodes.class.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the collection of attributes</b></td>
<td>
<b>Property</b>:<i>`nodes.class.attributes`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        attributes: [{ name: "accepted"}]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the name of the attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.class.attributes.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        attributes: [{ name: "accepted" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the data type of attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.class.attributes.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        attributes: [{ name: "accepted", type: "Date" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the visibility of the attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.class.attributes.scope`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        attributes: [{ name: "accepted", type: "Date", scope:"protected" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the collection of methods of a Class</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient", methods: [{ name: "getHistory" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the name of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
         methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }]
         }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the arguments of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.arguments`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{
                name: "Date",
                type:"String"
                }]
            }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the name, attributes and methods of a Class. Applicable, if the node is a Class</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.arguments.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        methods: [
            {
            name: "getHistory",
            arguments: [
                { name: "Date" }
                ],
            type: "History"
            }]
        }
    }];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the type of the argument</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.arguments.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        methods: [
            {
            name: "getHistory",
            arguments: [
                { name: "Date" }
                ],
            type: "History"
            }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the return type of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }],
            type: "History" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the visibility of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.class.methods.scope`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Class,
    "class": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }],
            type: "History",
            scope:"protected" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the state of the node is collapsed/expanded</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", fill: 'red' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp" }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border color for collapse icon of node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.borderColor`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            borderColor: "red"
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            borderColor: "red"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.borderColor`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", borderColor: 'red' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", borderColor: 'red' }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border width for collapse icon of node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.borderWidth`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            borderWidth: "2"
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            borderWidth: "2"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.borderWidth`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", borderWidth: '2' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", borderWidth: '2' }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the fill color for collapse icon of node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.fillColor`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            fillColor: "green"
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            fillColor: "green"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.fill`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", fill: 'red' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", fill: 'red' }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the height for collapse icon of node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.height`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", fill: 'red' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp" }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the icon</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.horizontalAlignment`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            horizontalAlignment:ej.datavisualization.Diagram.HorizontalAlignment.Left
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            horizontalAlignment:ej.datavisualization.Diagram.HorizontalAlignment.Left
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.horizontalAlignment`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", horizontalAlignment:'Center' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", horizontalAlignment:'Center' }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>To set the margin for the collapse icon of node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.margin`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            margin:{ left: 5 }
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            margin:{ left: 5 }
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.margin`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", fill: 'red',
        margin:{ left: 5 } },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp",
        margin:{ left: 5 } }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the fraction/ratio(relative to node) that defines the position of the icon</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.offset`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            offset:ej.datavisualization.Diagram.Point(0,0.5)
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "ArrowDown",
            offset:ej.datavisualization.Diagram.Point(0,0.5)
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.offset`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown",
        offset: { x: 0, y: 0.5 } },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp",
        offset: { x: 0, y: 0.5 } }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the shape of the collapsed state of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.shape`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "arrowdown"
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.shape`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", fill: 'red' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp" }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the vertical alignment of the icon</b></td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.verticalAlignment `</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        collapseIcon: {
            shape:"arrowup",
            width:10,
            height:10,
            verticalAlignment:ej.datavisualization.Diagram.VerticalAlignment.Top
            },
        expandIcon: {
            height: 10,
            width: 10,
            shape: "arrowdown",
            verticalAlignment:ej.datavisualization.Diagram.VerticalAlignment.Top
            }
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.verticalAlignment `</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", verticalAlignment: 'Center' },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", verticalAlignment: 'Center' }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b> Defines the custom content of the icon</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.content`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: {
            height: 20,
            width: 20,
            shape: "Template",
            content: '<g><path d="M90,43.841c0,24.213-19.779,43.841-44.182,43.841c-7.747,0-15.025-1.98-21.357-5.455L0,90l7.975-23.522' +
                'c-4.023-6.606-6.34-14.354-6.34-22.637C1.635,19.628,21.416,0,45.818,0C70.223,0,90,19.628,90,43.841z M45.818,6.982' +
                'c-20.484,0-37.146,16.535-37.146,36.859c0,8.065,2.629,15.534,7.076,21.61L11.107,79.14l14.275-4.537' +
                'c5.865,3.851,12.891,6.097,20.437,6.097c20.481,0,37.146-16.533,37.146-36.857S66.301,6.982,45.818,6.982z M68.129,53.938' +
                'c-0.273-0.447-0.994-0.717-2.076-1.254c-1.084-0.537-6.41-3.138-7.4-3.495c-0.993-0.358-1.717-0.538-2.438,0.537' +
                'c-0.721,1.076-2.797,3.495-3.43,4.212c-0.632,0.719-1.263,0.809-2.347,0.271c-1.082-0.537-4.571-1.673-8.708-5.333' +
                'c-3.219-2.848-5.393-6.364-6.025-7.441c-0.631-1.075-0.066-1.656,0.475-2.191c0.488-0.482,1.084-1.255,1.625-1.882' +
                'c0.543-0.628,0.723-1.075,1.082-1.793c0.363-0.717,0.182-1.344-0.09-1.883c-0.27-0.537-2.438-5.825-3.34-7.977' +
                'c-0.902-2.15-1.803-1.792-2.436-1.792c-0.631,0-1.354-0.09-2.076-0.09c-0.722,0-1.896,0.269-2.889,1.344' +
                'c-0.992,1.076-3.789,3.676-3.789,8.963c0,5.288,3.879,10.397,4.422,11.113c0.541,0.716,7.49,11.92,18.5,16.223' +
                'C58.2,65.771,58.2,64.336,60.186,64.156c1.984-0.179,6.406-2.599,7.312-5.107C68.398,56.537,68.398,54.386,68.129,53.938z">' +
                '</path></g>'
        },
        collapseIcon: {
            height: 20,
            width: 20,
            shape: "ArrowUp"
        }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the geometry of a path</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.pathData`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "Path", pathData: "M0,0 L0,100" },
        collapseIcon: { height: 20, width: 20, shape: "Path", pathData: "M0,0 L0,100" }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the corner radius of the icon border</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.cornerRadius`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", cornerRadius: 3},
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", cornerRadius: 3 }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the space that the icon has to be moved from the icon border</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.collapseIcon.padding`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        expandIcon: { height: 20, width: 20, shape: "ArrowDown", padding: { left: 50 } },
        collapseIcon: { height: 20, width: 20, shape: "ArrowUp", padding: { left: 50 } }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the distance to be left between a node and its connections(In coming and out going connections)</b></td>
<td>
<b>Property</b>:<i>`nodes.connectorPadding`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        connectorPadding: 5
    }],
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Enables or disables the default behaviors of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.constraints`</i>
</br>
</br>
<code>
var NodeConstraints = ej.datavisualization.Diagram.NodeConstraints;

$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        constraints: NodeConstraints.Default & ~NodeConstraints.Select
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        constraints: NodeConstraints.Default | NodeConstraints.Select
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines how the child objects need to be arranged(Either in any predefined manner or automatically). Applicable, if the node is a group</b></td>
<td>
<b>Property</b>:<i>`nodes.container`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var group = {
    name: "group",
    children: [node1, node2],
    container: {
        type: "stack"
    },
    offsetX: 200,
    offsetY: 100
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the orientation of the container. Applicable, if the group is a container</b></td>
<td>
<b>Property</b>:<i>`nodes.container.orientation`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var group = {
    name: "group",
    children: [node1, node2],
    container: {
        type: "stack",
        orientation: "horizontal"
    },
    offsetX: 200,
    offsetY: 100
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the type of the container. Applicable if the group is a container.</b></td>
<td>
<b>Property</b>:<i>`nodes.container.type`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    borderColor: "red",
    borderDashArray: "4,2"
};
var group = {
    name: "group",
    children: [node1, node2],
    container: {
        type: ej.datavisualization.Diagram.ContainerType.Stack
    },
    offsetX: 200,
    offsetY: 100
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the corner radius of rectangular shapes</b></td>
<td>
<b>Property</b>:<i>`nodes.cornerRadius`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        type:"basic",
        shape:"rectangle",
        cornerRadius:5
    }],
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>This property allows you to customize nodes appearance using user-defined CSS</b></td>
<td>
<b>Property</b>:<i>`nodes.cssClass`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        cssClass: "hoverNode"
    }],
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the BPMN data object</b></td>
<td>
<b>Property</b>:<i>`nodes.data.type`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
    name: "dataobject",
    type: "bpmn",
    shape: ej.datavisualization.Diagram.BPMNShapes.DataObject,
    data: {
        type: ej.datavisualization.Diagram.BPMNDataObjects.Input
    },
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100
}];
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.dataObject.type`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
    id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: false,
            type: 'Input'
        }
    }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether the BPMN data object is a collection or not</b></td>
<td>
<b>Property</b>:<i>`nodes.data.collection`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
    name: "dataobject",
    type: "bpmn",
    shape: ej.datavisualization.Diagram.BPMNShapes.DataObject,
    data: {
        type: ej.datavisualization.Diagram.BPMNDataObjects.Input,
        collection: false
    },
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100
}];
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.dataObject.collection`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
    id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 100,
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        dataObject: {
            collection: false,
            type: 'Input'
        }
    }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines an Enumeration in a UML Class Diagram</b></td>
<td>
<b>Property</b>:<i>`nodes.enumeration`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "Enums",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Enumeration,
    enumeration: {
        name: "AccountType",
    }
}]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the name of the Enumeration</b></td>
<td>
<b>Property</b>:<i>`nodes.enumeration.name`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "Enums",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Enumeration,
    enumeration: {
        name: "AccountType",
    }
}]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the collection of enumeration members</b></td>
<td>
<b>Property</b>:<i>`nodes.enumeration.members`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "Enums",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Enumeration,
    enumeration: {
        name: "AccountType",
        members: [{ name: "CheckingAccount"}]
    }
}]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the name of the enumeration member</b></td>
<td>
<b>Property</b>:<i>`nodes.enumeration.members.name`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "Enums",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.Enumeration,
    enumeration: {
        name: "AccountType",
        members: [{ name: "CheckingAccount"}]
    }
}]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the type of the BPMN Events. Applicable, if the node is a BPMN event</b></td>
<td>
<b>Property</b>:<i>`nodes.event`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "nodeEvent",
    type: "bpmn",
    shape: "event",
    event: ej.datavisualization.Diagram.BPMNEvents.Intermediate,
    width: 50,
    height: 50
}]
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.event`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        shape: {
            type: 'Bpmn', shape: 'Event',
            event: { event: 'Start', trigger: 'None' } }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the type of the trigger</b></td>
<td>
<b>Property</b>:<i>`nodes.event.trigger`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes : [{
    name: "nodeEvent",
    type: "bpmn",
    shape: ej.datavisualization.Diagram.BPMNShapes.Event,
    trigger: ej.datavisualization.Diagram.BPMNTriggers.None
    width: 50,
    height: 50
}]
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.event.trigger`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        shape: {
            type: 'Bpmn', shape: 'Event',
            event: { event: 'Start', trigger: 'None' } }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether the node can be automatically arranged using layout or not</b></td>
<td>
<b>Property</b>:<i>`nodes.excludeFromLayout`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    excludeFromLayout: true
};

var node2 = {
    name: "node2",
    width: 50,
    height: 50
};
var node3 = {
    name: "node3",
    width: 50,
    height: 50
};

$("#diagramcontent").ejDiagram({
    nodes: [node1, node2, node3],
    layout: {
        type: "hierarchicaltree"
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.excludeFromLayout`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        excludeFromLayout: true,
    },
    { id: 'node1', width: 70, height: 70, annotations: [{ content: 'node1' }] },
    { id: 'node2', width: 70, height: 70, annotations: [{ content: 'node2' }] };
],
    layout: {
    type: 'RadialTree',
},
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the fill color of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.fillColor`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    fillColor:"red"};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.fill`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        style: { fill: 'red' }
        },
],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the type of the BPMN Gateway. Applicable, if the node is a BPMN gateway</b></td>
<td>
<b>Property</b>:<i>`nodes.gateway`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "gateway" ,
    gateway: ej.datavisualization.Diagram.BPMNGateways.Exclusive
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.gateway`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node', width: 100, height: 100, offsetX: 100, offsetY: 100,
        shape: { type: 'Bpmn', shape: 'Gateway', gateway: { type: 'Exclusive' }
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Paints the node with linear color transitions</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.type`</i>
</br>
</br>
<code>
var gradient = {
    type: "linear",
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: [{
        color: "white",
        offset: 0
    }, {
        color: "red",
        offset: 50
    }]
};
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    gradient : gradient
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.type`</i>
</br>
</br>
<code>
var stopscol = [];
var stops1 = {
    color: 'white',
    offset: 0
};
stopscol.push(stops1);
var stops2 = {
    color: 'red',
    offset: 50
};
stopscol.push(stops2);
var gradient1 = {
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: stopscol,
    type: 'Linear'
};

var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient1
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the x1 value of linear gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.LinearGradient.x1`</i>
</br>
</br>
<code>
var gradient = {
    type: "linear",
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: [{
        color: "white",
        offset: 0
    }, {
        color: "red",
        offset: 50
    }]
};
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    gradient : gradient
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.LinearGradient.x1`</i>
</br>
</br>
<code>
var stopscol = [];
var stops1 = {
    color: 'white',
    offset: 0
};
stopscol.push(stops1);
var stops2 = {
    color: 'red',
    offset: 50
};
stopscol.push(stops2);
var gradient1 = {
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: stopscol,
    type: 'Linear'
};

var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient1
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the x2 value of linear gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.LinearGradient.x2`</i>
</br>
</br>
<code>
var gradient = {
    type: "linear",
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: [{
        color: "white",
        offset: 0
    }, {
        color: "red",
        offset: 50
    }]
};
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    gradient : gradient
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.LinearGradient.x2`</i>
</br>
</br>
<code>
var stopscol = [];
var stops1 = {
    color: 'white',
    offset: 0
};
stopscol.push(stops1);
var stops2 = {
    color: 'red',
    offset: 50
};
stopscol.push(stops2);
var gradient1 = {
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: stopscol,
    type: 'Linear'
};

var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient1
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the y1 value of linear gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.LinearGradient.y1`</i>
</br>
</br>
<code>
var gradient = {
    type: "linear",
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: [{
        color: "white",
        offset: 0
    }, {
        color: "red",
        offset: 50
    }]
};
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    gradient : gradient
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.LinearGradient.y1`</i>
</br>
</br>
<code>
var stopscol = [];
var stops1 = {
    color: 'white',
    offset: 0
};
stopscol.push(stops1);
var stops2 = {
    color: 'red',
    offset: 50
};
stopscol.push(stops2);
var gradient1 = {
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: stopscol,
    type: 'Linear'
};

var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient1
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the y2 value of linear gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.LinearGradient.y2`</i>
</br>
</br>
<code>
var gradient = {
    type: "linear",
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: [{
        color: "white",
        offset: 0
    }, {
        color: "red",
        offset: 50
    }]
};
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    gradient : gradient
    };

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.LinearGradient.y2`</i>
</br>
</br>
<code>
var stopscol = [];
var stops1 = {
    color: 'white',
    offset: 0
};
stopscol.push(stops1);
var stops2 = {
    color: 'red',
    offset: 50
};
stopscol.push(stops2);
var gradient1 = {
    x1: 0,
    x2: 50,
    y1: 0,
    y2: 50,
    stops: stopscol,
    type: 'Linear'
};

var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient1
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the type of gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.type`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.type`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the position of the outermost circle
</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.cx`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.RadialGradient.cx`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the outer most circle of the radial gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.cy`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.RadialGradient.cy`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the innermost circle of the radial gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.fx`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.RadialGradient.fx`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the innermost circle of the radial gradient</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.fy`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.RadialGradient.fy`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the different colors and the region of color transitions</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.RadialGradient.stops`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.RadialGradient.stops`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the color to be filled over the specified region</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.stops.color`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.stops.color`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the position where the previous color transition ends and a new color transition starts</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.stops.offset`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.stops.offset`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Describes the transparency level of the region</b></td>
<td>
<b>Property</b>:<i>`nodes.gradient.stops.opacity`</i>
</br>
</br>
<code>
var node = {
    name: "node",
    width: 50,
    height: 50,
    offsetX: 100,
    offsetY: 100,
    gradient: {
        type: "radial",
        fx: 50,
        fy: 50,
        cx: 50,
        cy: 50,
        stops: [{
            color: "white",
            offset: 0
        }, {
            color: "red",
            offset: 100,
            opacity: 0.5
        }]
    }
};

$("#diagramcontent").ejDiagram({
    nodes: [node1],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.gradient.stops.opacity`</i>
</br>
</br>
<code>
var stops = [{
    color: 'white',
    offset: 0
}, {
    color: 'red',
    offset: 50,
    opacity: 0.5
}];
var gradient = {
    cx: 50,
    cy: 50,
    fx: 50,
    fy: 50,
    stops: stops,
    type: 'Radial'
};
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node',
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        style: {
            gradient: gradient
        }
    }],
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the header of a swimlane/lane</b></td>
<td>
<b>Property</b>:<i>`nodes.header`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    header: {
        text: "Swimlane",
        fontSize: 12,
        bold: true
    }
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the height of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.height`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the node. Applicable, if the parent of the node is a container</b></td>
<td>
<b>Property</b>:<i>`nodes.horizontalAlign`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    horizontalAlign: ej.datavisualization.Diagram.HorizontalAlignment.Right
};
var group = {
    name: "group",
    children: [node1, node2],
    container: {
        type: "canvas"
    },
    offsetX: 200,
    offsetY: 100,
    minWidth: 200,
    minHeight: 200,
    fillColor: "red"
};
$("#diagramcontent").ejDiagram({
    nodes: [group]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A read only collection of the incoming connectors/edges of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.inEdges`</i>
</br>
</br>
<code>
var node = diagram.selectionList[0];
for(var i = 0; i < node.inEdges.length; i++){
    console.log(node.inEdges[i]);
};
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.inEdges`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
var node = (diagram.nodes[0] as Node).inEdges;
for (var i = 0; i < node.length; i++) {
console.log(node[i]);
};
</code></td>
</tr>

<tr>
<td><b>Defines an interface in a UML interface Diagram</b></td>
<td>
<b>Property</b>:<i>`nodes.interface`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient", offsetX: 100, offsetY: 100, borderWidth: 2, borderColor: "black",
    type: "umlclassifier", classifier: ej.datavisualization.Diagram.ClassifierShapes.interface
    }];
$("#diagramcontent").ejDiagram({ nodes:nodes });
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the name, attributes and methods of a Interface. Applicable, if the node is a Interface</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the collection of attributes</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.attributes`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        attributes: [{ name: "accepted"}]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the name of the attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.attributes.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        attributes: [{ name: "accepted" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the data type of attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.attributes.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        attributes: [{ name: "accepted", type: "Date" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the visibility of the attribute</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.attributes.scope`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        attributes: [{ name: "accepted", type: "Date", scope:"protected" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the collection of methods of a interface</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient", methods: [{ name: "getHistory" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the name of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
         methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }]
         }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the arguments of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.arguments`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{
                name: "Date",
                type:"String"
                }]
            }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Defines the name, attributes and methods of a interface. Applicable, if the node is a interface</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.arguments.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        methods: [
            {
            name: "getHistory",
            arguments: [
                { name: "Date" }
                ],
            type: "History"
            }]
        }
    }];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the type of the argument</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.arguments.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        methods: [
            {
            name: "getHistory",
            arguments: [
                { name: "Date" }
                ],
            type: "History"
            }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the return type of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.type`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }],
            type: "History" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
<tr>
<td><b>Sets the visibility of the method</b></td>
<td>
<b>Property</b>:<i>`nodes.interface.methods.scope`</i>
</br>
</br>
<code>
var nodes = [{
    name: "Patient",
    offsetX: 100,
    offsetY: 100,
    borderWidth: 2,
    borderColor: "black",
    type: "umlclassifier",
    classifier: ej.datavisualization.Diagram.ClassifierShapes.interface,
    "interface": {
        name: "Patient",
        methods: [{
            name: "getHistory",
            arguments: [{name: "Date" }],
            type: "History",
            scope:"protected" }]
    }
}];
$("#DiagramContent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines whether the sub tree of the node is expanded or collapsed</b></td>
<td>
<b>Property</b>:<i>`nodes.isExpanded`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    isExpanded: false
};

var node2 = {
    name: "node2",
    width: 50,
    height: 50
};
var connector = {
    sourceNode: "node1",
    targetNode: "node2",
    name: "connector"
};
$("#diagramcontent").ejDiagram({
    nodes: [node1, node2],
    connectors: [connector],
    layout: {
        type: "hierarchicaltree"
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.isExpanded`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        id: 'node1',
        isExpanded: true,
    },
    {
    id: 'node2',
    width: 50,
    height: 50
    }],
    connectors: [{
        sourceNode: 'node1',
        targetNode: 'node2',
        id: 'connector'
    }],
    layout: {
        type: "hierarchicaltree"
    }
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the node as a swimlane</b></td>
<td>
<b>Property</b>:<i>`nodes.isSwimlane`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    isSwimlane: true,
    header: {
        text: "Swimlane",
        fontSize: 12,
        bold: true
    }
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A collection of objects where each object represents a label</b></td>
<td>
<b>Property</b>:<i>`nodes.labels`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                fontColor: "Red"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.annotations`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation'
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>An array of objects where each object represents a lane. Applicable, if the node is a swimlane</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200
        },
        {
            name: "lane2",
            width: 100
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>This property allows you to customize lanes appearance using user-defined CSS</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes.cssClass`</i>
</br>
</br>
<code>
var addInfo = { Description:"Describe the functionality" };
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200
        },
        {
            name: "lane2",
            width: 100,
            cssClass:"hoverLane",
            addInfo: addInfo,
            fillColor:"lightgrey"
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the header of the lane</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes.header`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200
        },
        {
            name: "lane2",
            width: 100,
            header: {
                fillColor:"blue",
                fontColor:"white",
                text:"Function 1"
                }
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the width of lane</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes.width`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200,
            height: 200,
            zOrder:10
        },
        {
            name: "lane2",
            width: 100
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>An array of objects where each object represents a child node of the lane</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes.children`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200
        },
        {
            name: "lane2",
            width: 100,
            children:[{name:"process", width: 50, height: 50 }]
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the object as a lane</b></td>
<td>
<b>Property</b>:<i>`nodes.lanes.isLane`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
            name: "lane1",
            width: 200,
            height: 200,
            isLane:true,
            orientation:"vertical"
        },
        {
            name: "lane2",
            width: 100
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the minimum space to be left between the bottom of parent bounds and the node</b></td>
<td>
<b>Property</b>:<i>`nodes.margin`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 200,
    lanes: [{
        name: "lane1",
        width: 200,
        children: [{
            name: "process",
            width: 50,
            height: 50,
            marginBottom: 50,
            marginLeft: 10,
            marginRight: 10,
            marginTop: 10
        }]
    }]
}
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.margin`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        margin : { left: 15, right: 15, top: 15, bottom: 15 }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the maximum height limit of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.maxHeight`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    maxHeight: 100,
    maxWidth: 100,
    minHeight: 10,
    minWidth: 10
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.maxHeight`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        maxHeight: 100,
        maxWidth: 100,
        minHeight: 10,
        minWidth: 10
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the unique identifier of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.name`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.id`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node1'
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the opaque of the node</b></td>
<td>
<b>Property</b>:<i>`nodes.opacity`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    opacity: 0.5,
    rotateAngle: 70
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.style.opacity`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        id: 'node1'
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        rotateAngle: 70,
        style: {
            opacity: 0.5
        }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the minimum padding value to be left between the bottom most position of a group and its children. Applicable, if the group is a container</b></td>
<td>
<b>Property</b>:<i>`nodes.paddingBottom`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    verticalAlign: "bottom"
};
var group = {
    name: "group",
    children: [node1, node2],
    container: {
        type: "canvas"
    },
    offsetX: 200,
    offsetY: 100,
    fillColor: "gray",
    minWidth: 200,
    minHeight: 200,
    paddingBottom: 10,
    paddingLeft: 10,
    paddingRight: 10,
    paddingTop: 10
};
$("#diagramcontent").ejDiagram({nodes:[group]});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the name of the parent group</b></td>
<td>
<b>Property</b>:<i>`nodes.parent`</i>
</br>
</br>
<code>
var node1 = {
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    parent: "group"
};
var node2 = {
    name: "node2",
    width: 50,
    height: 50,
    offsetX: 150,
    offsetY: 150,
    parent: "group"
};

var group = {
    name: "group",
    children: ["node1", "node2"]
};
$("#diagramcontent").ejDiagram({
    nodes: [node1, node2, group]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Sets the path geometry that defines the shape of a path node</b></td>
<td>
<b>Property</b>:<i>`nodes.pathData`</i>
</br>
</br>
<code>
var nodes;
nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    type: "basic",
    shape: "path",
    pathData: "M 370.9702,194.9961 L 359.5112,159.7291 L 389.5112,137.9341 L 419.5112,159.7291 L 408.0522,194.9961 L 370.9702,194.9961 z"
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.data`</i>
</br>
</br>
<code>
var nodes = [
    {
        id: 'node1', width: 100, height: 100, offsetX: 300, offsetY: 100,
        shape: { type: 'Path', data: 'M 540.3643,137.9336 L 546.7973,159.7016 L 570.3633,159.7296 L 550.7723,171.9366 L 558.9053,194.9966 L 540.3643,179.4996 L 521.8223,194.9966 L 529.9553,171.9366 L 510.3633,159.7296 L 533.9313,159.7016 L 540.3643,137.9336 z' },
    },
];

var diagram = new ej.diagrams.Diagram({
    width: '800px', height: '500px', nodes: nodes
});
</code></td>
</tr>

<tr>
<td><b>An array of objects, where each object represents a smaller region(phase) of a swimlane</b></td>
<td>
<b>Property</b>:<i>`nodes.phases`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 100,
    width: 300,
    orientation: "horizontal",
    phases: [{
            name: "phase1",
            offset: 150,
            label: {
                text: "Phase1"
            }
        },
        {
            name: "phase2",
            label: {
                text: "Phase2"
            }
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the header of the smaller regions</b></td>
<td>
<b>Property</b>:<i>`nodes.phases.label`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 100,
    width: 300,
    orientation: "horizontal",
    phases: [{
            name: "phase1",
            offset: 150,
            label: {
                text: "Phase1"
            }
        },
        {
            name: "phase2",
            label: {
                text: "Phase2"
            }
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the line color of the splitter that splits adjacent phases</b></td>
<td>
<b>Property</b>:<i>`nodes.phases.lineColor`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 100,
    width: 300,
    orientation: "horizontal",
    phases: [{
            name: "phase1",
            offset: 150,
            label: {
                text: "Phase1"
            },
            lineColor:"green",
            lineDashArray:"2,2",
            lineWidth:3
        },
        {
            name: "phase2",
            label: {
                text: "Phase2"
            }
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the length of the smaller region(phase) of a swimlane</b></td>
<td>
<b>Property</b>:<i>`nodes.phases.offset`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 100,
    width: 300,
    orientation: "horizontal",
    phases: [{
            name: "phase1",
            offset: 150,
            label: {
                text: "Phase1"
            }
        },
        {
            name: "phase2",
            label: {
                text: "Phase2"
            }
        }
    ]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the orientation of the phase</b></td>
<td>
<b>Property</b>:<i>`nodes.phases.orientation`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
diagram.addPhase(diagram.selectionList[0].name,
{
    name: "verticalPhase",
    type: "phase", offset: 200, orientation: "vertical",
    label: { text: "New Phase" }
    } );
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the height of the phase headers</b></td>
<td>
<b>Property</b>:<i>`nodes.phaseSize`</i>
</br>
</br>
<code>
var swimlane = {
    type: "swimlane",
    name: "swimlane",
    offsetX: 300,
    offsetY: 100,
    width: 300,
    orientation: "horizontal",
    phaseSize: 50,
    phases: [{
        name: "phase1",
        offset: 150,
        label: {
            text: "Phase 1"
        }
    }]
};
$("#diagramcontent").ejDiagram({
    nodes: [swimlane]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the ratio/ fractional value relative to node, based on which the node will be transformed(positioning, scaling and rotation)</b></td>
<td>
<b>Property</b>:<i>`nodes.pivot`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    pivot: {
        x: 0,
        y: 0
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.pivot`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        pivot: {
            x: 0,
            y: 0
        }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines a collection of points to draw a polygon. Applicable, if the shape is a polygon</b></td>
<td>
<b>Property</b>:<i>`nodes.points`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    type: "basic",
    shape: "polygon",
    points: [{
        x: 0,
        y: 12.5
    }, {
        x: 0,
        y: 50
    }, {
        x: 50,
        y: 50
    }, {
        x: 50,
        y: 0
    }, {
        x: 12.5,
        y: 0
    }, {
        x: 0,
        y: 12.5
    }]
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.points`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        shape: {
            type: 'Basic',
            shape: 'Polygon',
            points: [{
                x: 35,
                y: 0
            }, {
                x: 65,
                y: 0
            }, {
                x: 100,
                y: 35
            }, {
                x: 100,
                y: 65
            }, {
                x: 65,
                y: 100
            }, {
                x: 35,
                y: 100
            }, {
                x: 0,
                y: 65
            }, {
                x: 0,
                y: 35
            }]
        },
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>An array of objects where each object represents a port</b></td>
<td>
<b>Property</b>:<i>`nodes.ports`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    ports: [{
            name: "port1",
            offset: {
                x: 0.5,
                y: 0
            }
        },
        {
            name: "port2",
            offset: {
                x: 0.5,
                y: 1
            }
        }
    ]
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.ports`</i>
</br>
</br>
<code>
var port = [{
    id: 'port1',
    visibility: PortVisibility.Visible,
    shape: 'Circle',
    offset: {
        x: 0,
        y: 0
    }
}];
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        ports: port
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border color of the port</b></td>
<td>
<b>Property</b>:<i>`nodes.ports.borderColor`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    ports: [{
            name: "port1",
            offset: {
                x: 0.5,
                y: 0
            },
            borderColor:"yellow",
            borderWidth: 3,
            cssClass:"hoverPort",
            fillColor:"red",
            size: 10,
            visibility:ej.datavisualization.Diagram.PortVisibility.Visible
        },
        {
            name: "port2",
            offset: {
                x: 0.5,
                y: 1
            }
        }
    ]
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.ports.style.strokeColor`</i>
</br>
</br>
<code>
var port = [{
    id: 'port1',
    visibility: PortVisibility.Visible,
    shape: 'Circle',
    offset: {
        x: 0,
        y: 0
    },
    style: {
        strokeColor: 'yellow',
        strokeDashArray: '2 2',
        strokeWidth: 4,
        fill:'red',
        opacity: 0.5
    }
}];
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        ports: port
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether connections can be created with the port</b></td>
<td>
<b>Property</b>:<i>`nodes.ports.constraints`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    ports: [{
            name: "port1",
            offset: {
                x: 0.5,
                y: 0
            }
        },
        {
            name: "port2",
            offset: {
                x: 0.5,
                y: 1
            }
        }
    ]
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.ports.constraints`</i>
</br>
</br>
<code>
var port = [{
    id: 'port1',
    visibility: PortVisibility.Visible,
    shape: 'Circle',
    offset: {
        x: 0,
        y: 0
    },
    constraints: PortConstraints.Draw
}];
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        ports: port
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>An array of objects where each object represents a port</b></td>
<td>
<b>Property</b>:<i>`nodes.ports.shape`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    ports: [{
            name: "port1",
            offset: {
                x: 0.5,
                y: 0
            },
            shape:ej.datavisualization.Diagram.PortShapes.Path,
            pathData: "M5,0 L10,10 L0,10 z"
        },
        {
            name: "port2",
            offset: {
                x: 0.5,
                y: 1
            }
        }
    ]
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.ports.shape`</i>
</br>
</br>
<code>
var port = [{
    id: 'port1',
    visibility: PortVisibility.Visible,
    shape: 'Path',
    pathData: 'M5,0 L10,10 L0,10 z'
    offset: {
        x: 0,
        y: 0
    }
}];
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        ports: port
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the vertical alignment of the port with respect to its immediate parent</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`nodes.ports.verticalAlignment`</i>
</br>
</br>
<code>
var port = [{
    id: 'port1',
    visibility: PortVisibility.Visible,
    shape: 'Circle',
    offset: {
        x: 0,
        y: 0
    },
    verticalAlignment: 'Top',
    horizontalAlignment: 'Left',
    width: 10,
    height: 10
}];
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        ports: port
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the opacity and the position of shadow</b></td>
<td>
<b>Property</b>:<i>`nodes.shadow`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 50,
    height: 50,
    offsetX: 50,
    offsetY: 50,
    shadow: { opacity: 0.5, distance: 10, angle: 45 }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});
</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shadow`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        shadow: { opacity: 0.5, distance: 10, angle: 45 }
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the sub process of a BPMN Activity. Applicable, if the type of the BPMN activity is sub process</b></td>
<td>
<b>Property</b>:<i>`nodes.subProcess`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 100,
    height: 100,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "activity",
    activity: "subprocess",
    subProcess: {
        loop: ej.datavisualization.Diagram.BPMNLoops.Standard,
        adhoc: true,
        boundary: ej.datavisualization.Diagram.BPMNBoundary.Call,
        compensation: true,
        collapsed: false
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity.subProcess`</i>
</br>
</br>
<code>
var nodes = [{
    id: 'node',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        activity: {
            activity: 'SubProcess',
            subProcess: { adhoc: false, boundary: 'Default', collapsed: true }
        }
    }
}];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the collection of events that need to be appended with BPMN Sub-Process</b></td>
<td>
<b>Property</b>:<i>`nodes.subProcess.events`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 100,
    height: 100,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "activity",
    activity: "subprocess",
    subProcess: {
        type: "transaction",
        events: [{
                name:"intermediate1",
                event: "intermediate",
                offset: {
                    x: 0.25,
                    y: 1
                }
            },
            {
                event: "intermediate",
                trigger: "error",
                offset: {
                    x: 0.75,
                    y: 1
                }
            }
        ]
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity.subProcess.events`</i>
</br>
</br>
<code>
var nodes = [{
          id: 'node1', width: 190, height: 190, offsetX: 300, offsetY: 200,
          shape: {
              type: 'Bpmn', shape: 'Activity', activity: {
                  activity: 'SubProcess',
                  subProcess: {
                      type: 'Event', loop: 'ParallelMultiInstance',
                      compensation: true, adhoc: false, boundary: 'Event', collapsed: true,
                      events: [{
                          height: 20, width: 20, offset: { x: 0, y: 0 }, margin: { left: 10, top: 10 },
                          horizontalAlignment: 'Left',
                          verticalAlignment: 'Top',
                          event: 'Intermediate', trigger: 'Error'
                      }]
                  }
              }
          }
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>An array of objects where each object represents a port</b></td>
<td>
<b>Property</b>:<i>`nodes.subProcess.events.ports`</i>
</br>
</br>
<code>
var nodes;
nodes = [{
    name: "node1",
    width: 100,
    height: 100,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "activity",
    activity: "subprocess",
    subProcess: {
        type: "transaction",
        events: [{
            event: "intermediate",
            offset: {
                x: 0.25,
                y: 1
            },
            ports: [{
                    name: "port1",
                    offset: {
                        x: 0.5,
                        y: 0
                    }
                },
                {
                    name: "port2",
                    offset: {
                        x: 0.5,
                        y: 1
                    }
                }
            ]
        }]
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity.subProcess.events.ports`</i>
</br>
</br>
<code>
var nodes = [{
          id: 'node1', width: 190, height: 190, offsetX: 300, offsetY: 200,
          shape: {
              type: 'Bpmn', shape: 'Activity', activity: {
                  activity: 'SubProcess',
                  subProcess: {
                      type: 'Event', loop: 'ParallelMultiInstance',
                      compensation: true, adhoc: false, boundary: 'Event', collapsed: true,
                      events: [{
                          height: 20, width: 20, offset: { x: 0, y: 0 }, margin: { left: 10, top: 10 },
                          horizontalAlignment: 'Left',
                          verticalAlignment: 'Top',
                          ports: [{
                              id: 'port1', visibility: PortVisibility.Visible,
                              shape: 'Circle', offset: { x: 0, y: 0 }
                          }],
                          event: 'Intermediate', trigger: 'Error'
                      }]
                  }
              }
          }
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>A collection of objects where each object represents a label</b></td>
<td>
<b>Property</b>:<i>`nodes.subProcess.events.labels`</i>
</br>
</br>
<code>
var label = [];
label = { "text": "Node1", "fontColor": "Red"};
var nodes = [{
    name: "node1",
    width: 100,
    height: 100,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "activity",
    activity: "subprocess",
    subProcess: {
        type: "transaction",
        events: [{
            event: "intermediate",
            offset: {
                x: 0.25,
                y: 1
            },
            {labels:label}
        }]
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity.subProcess.events.annotations`</i>
</br>
</br>
<code>
var nodes = [{
          id: 'node1', width: 190, height: 190, offsetX: 300, offsetY: 200,
          shape: {
              type: 'Bpmn', shape: 'Activity', activity: {
                  activity: 'SubProcess',
                  subProcess: {
                      type: 'Event', loop: 'ParallelMultiInstance',
                      compensation: true, adhoc: false, boundary: 'Event', collapsed: true,
                      events: [{
                          height: 20, width: 20, offset: { x: 0, y: 0 }, margin: { left: 10, top: 10 },
                          horizontalAlignment: 'Left',
                          verticalAlignment: 'Top',
                          annotations: [{
                              id: 'label3', margin: { bottom: 10 },
                               horizontalAlignment: 'Center',
                              verticalAlignment: 'Top',
                              content: 'Event', offset: { x: 0.5, y: 1 },
                              style: {
                                  color: 'black', fontFamily: 'Fantasy', fontSize: 8
                              }
                          }],
                          event: 'Intermediate', trigger: 'Error'
                      }]
                  }
              }
          }
      }];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the task of the BPMN activity. Applicable, if the type of activity is set as task</b></td>
<td>
<b>Property</b>:<i>`nodes.task`</i>
</br>
</br>
<code>
var nodes = [{
    name: "node1",
    width: 100,
    height: 100,
    offsetX: 50,
    offsetY: 50,
    type: "bpmn",
    shape: "activity",
    activity: "task",
    task: {
        compensation: true,
        call: true,
        loop: ej.datavisualization.Diagram.BPMNLoops.Standard,
        type: ej.datavisualization.Diagram.BPMNTasks.Service
    }
}];
$("#diagramcontent").ejDiagram({
    nodes: nodes
});</code>
</td>
<td>
<b>Property</b>:<i>`nodes.shape.activity.task`</i>
</br>
</br>
<code>
var nodes = [{
    id: 'node',
    width: 100,
    height: 100,
    offsetX: 100,
    offsetY: 100,
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        activity: {
            activity: 'Task',
            task: {
                call: true,
                compensation: false,
                type: 'Service',
                loop: 'ParallelMultiInstance'
            }
        }
    }
}];
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    nodes: nodes
});
diagram.appendTo('#diagram');
diagram.tool = DiagramTools.ZoomPan;
</code></td>
</tr>
</table>

## NodeTemplate

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Binds the custom JSON data with node properties</b></td>
<td>
<b>Property</b>:<i>`nodeTemplate`</i>
</br>
</br>
<code>
var data = [{
        "Id": "E1",
        "Name": "Maria Anders",
        "Designation": "Managing Director"
    },
    {
        "Id": "E2",
        "Name": "Ana Trujillo",
        "Designation": "Project Manager",
        "ReportingPerson": "E1"
    }
];

$("#diagramcontent").ejDiagram({
    dataSourceSettings: {
        id: "Id",
        parent: "ReportingPerson",
        dataSource: data
    },
    nodeTemplate: "nodeTemplate"
});

function nodeTemplate(diagram, node) {
    node.labels[0].text = node.Name;
}</code>
</td>
<td>
<b>Property</b>:<i>`setNodeTemplate`</i>
</br>
</br>
<code>
function setNodeTemplate() {
    setNodeTemplate: (object: NodeModel, diagram: Diagram): StackPanel => {
        if (object.id === 'node2') {
            var table = new StackPanel();
            table.orientation = 'Horizontal';
            var column1 = new StackPanel();
            column1.children = [];
            column1.children.push(getTextElement('Column1'));
            addRows(column1);
            var column2 = new StackPanel();
            column2.children = [];
            column2.children.push(getTextElement('Column2'));
            addRows(column2);
            table.children = [column1, column2];
            return table;
        }
        return null;
    }
}
var getTextElement = (text: string) => {
    var textElement = new TextElement();
    textElement.width = 50;
    textElement.height = 20;
    textElement.content = text;
    return textElement;
};
var nodes = [{
        id: 'node1',
        height: 100,
        offsetX: 100,
        offsetY: 100,
    },
    {
        id: 'node2',
        width: 100,
        height: 100,
        offsetX: 300,
        offsetY: 100
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
var diagram = new ej.diagrams.Diagram({
            width: '100%',
            height: '600px',
            connectors: connectors,
            nodes: nodes,
            setNodeTemplate: setNodeTemplate,
        });
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## Overview

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allows to see a preview or an overall view of the entire content of a Diagram</b></td>
<td>
<b>Property</b>:<i>`overview`</i>
</br>
</br>
<code>

<!--Initializes the Diagram element-->
<div id="diagram"></div>;

<!-- Initializes the overview element -->
<div id="overview"></div>;

<!--Initializes the Diagram control-->
$("#diagram").ejDiagram({
    width: "100%",
    height: "600px"
});

<!--Initializes the overview control-->
$("#overview").ejOverview({
    // Relates Diagram with overview
    sourceID: "diagram",
    width: "100%",
    height: "100%"
    });
</code>
</td>
<td>
<b>Property</b>:<i>`Overview`</i>
</br>
</br>
<code>
// Initializes the diagram control
var diagram = new ej.diagrams.Diagram({
    width: "100%",
    height: "600px"
});

diagram.appendTo('#diagram');
var overview = new ej.diagrams.Overview({
        width: '100%', height: '150px', sourceID: 'diagram'
    });
overview.appendTo('#overview');
</code></td>
</tr>
</table>

## Layers

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>A collection of JSON objects where each object represents a layer. Layer is a named category of diagram shapes</b></td>
<td>
<b>Property</b>:<i>`layers`</i>
</br>
</br>
<code>
var layer = {
    name: "layer1",
    active: true,
    visible: true,
    print: true,
    lock: true,
    objects: ["textNode"]
};
$("#diagram").ejDiagram({
    layers: [layer]
});
</code>
</td>
<td>
<b>Property</b>:<i>`layers`</i>
</br>
</br>
<code>
var nodes = [{
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
        offsetX: 300,
        offsetY: 100,
        shape: {
            type: 'Basic',
            shape: 'Ellipse'
        },
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
var diagram = new ej.diagrams.Diagram({
    width: '100%',
    height: '600px',
    connectors: connectors,
    nodes: nodes,
    layers: [{
        id: 'layer1',
        visible: true,
        lock: true,
        zIndex: -1,
        objects: ['node1', 'node2', 'connector1']
    }],

});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>A collection of JSON objects where each object represents a layer. Layer is a named category of diagram shapes</b></td>
<td>
<b>Property</b>:<i>`layers.print`</i>
</br>
</br>
<code>
var layer = { name: "layer1", active: true, visible: true, print: true, lock: true, objects: ["textNode"] };
$("#diagram").ejDiagram({
    layers: [layer]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
</table>

## Annotations

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>A collection of objects where each object represents a label</b></td>
<td>
<b>Property</b>:<i>`labels.text`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.content`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation'
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Offset for annotation content</b></td>
<td>
<b>Property</b>:<i>`labels.offset`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                offset: { x: 0, y: 1},
                rotateAngle: 90
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.offset`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            offset: { x: 0, y: 1},
            rotateAngle: 90
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the hyperlink for the labels</b></td>
<td>
<b>Property</b>:<i>`labels.hyperText`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                bold:true,
                "hyperText": "https://www.syncfusion.com"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.hyperlink`</i>
</br>
</br>
<code>
var style = { bold: true };
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: style,
            hyperlink: { color: 'red',
            content: 'HRPortal',
            textDecoration: 'Overline',
            link: 'https://hr.syncfusion.com/home' }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables/disables the bold style</b></td>
<td>
<b>Property</b>:<i>`labels.bold`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                bold:true
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.bold`</i>
</br>
</br>
<code>
var style = { bold: true };
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: style
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border color of the label</b></td>
<td>
<b>Property</b>:<i>`labels.borderColor`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                borderColor:"red",
                borderWidth: 2
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.borderColor`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                strokeColor: 'black',
                strokeWidth: 2
            }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the border width of the label</b></td>
<td>
<b>Property</b>:<i>`labels.borderWidth`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                borderColor: 'black',
                borderWidth: 2
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.borderWidth`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                        color: 'black',
                        fill: 'white',
                        opacity: 0.7,
                        strokeColor: 'black',
                        strokeWidth: 2
                    }
                }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>This property allows you to customize labels appearance using user-defined CSS</b></td>
<td>
<b>Property</b>:<i>`labels.cssClass`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                cssClass:"hoverText"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Enables or disables the default behaviors of the label</b></td>
<td>
<b>Property</b>:<i>`labels.constraints`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                constraints: LabelConstraints.All & ~LabelConstraints.Resizable
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            constraints: ~AnnotationConstraints.InheritReadOnly
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the fill color of the text area</b></td>
<td>
<b>Property</b>:<i>`labels.fillColor`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                fillColor: "green"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.fill`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                color: 'black',
                fill: 'white',
        }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the font color of the text</b></td>
<td>
<b>Property</b>:<i>`labels.fontColor`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                fontColor: "green"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.color`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                color: 'black',
        }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the font family of the text</b></td>
<td>
<b>Property</b>:<i>`labels.fontFamily`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                fontColor: "green",
                fontFamily:"seugoe UI",
                fontSize: 14
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.fontFamily`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                color: 'black',
                bold: true,
                italic: true,
                fontSize: '12',
                fontFamily: 'TimesNewRoman'
        }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the height of the label</b></td>
<td>
<b>Property</b>:<i>`labels.height`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                height: 100,
                width: 100
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            height: 100,
            width: 100
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the label</b></td>
<td>
<b>Property</b>:<i>`labels.horizontalAlignment`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                verticalAlignment:ej.datavisualization.Diagram.VerticalAlignment.Top,
                horizontalAlignment:ej.datavisualization.Diagram.HorizontalAlignment.Left
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.horizontalAlignment`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            horizontalAlignment: 'Left',
            verticalAlignment: 'Top'
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>To set the margin of the label</b></td>
<td>
<b>Property</b>:<i>`labels.margin`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                margin:{ left: 5 },
                padding:{ left: 5 }
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.margin`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            margin:{ left: 5 }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines whether the label is editable or not</b></td>
<td>
<b>Property</b>:<i>`labels.readOnly`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                readOnly:true
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            constraints: AnnotationConstraints.ReadOnly
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the id of svg/html templates. Applicable, if the node’s label is HTML or native</b></td>
<td>
<b>Property</b>:<i>`labels.templateId`</i>
</br>
</br>
<code>
<script id="SvgEllipse" type="text/x-jsrender">
        <svg xmlns="http://www.w3.org/2000/svg"
             xmlns:xlink="http://www.w3.org/1999/xlink">
            <circle cx="10" cy="6" r="5"
                     style="stroke:#006600; fill:#00cc00" />
        </svg>
</script>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                templateId:"SvgEllipse"
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines how to align the text inside the label</b></td>
<td>
<b>Property</b>:<i>`labels.textAlign`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                textAlign:ej.datavisualization.Diagram.TextAlign.Left,
                textDecoration: ej.datavisualization.Diagram.TextDecorations.Underline,
                textOverflow:true,
                overflowType: ej.datavisualization.Diagram.OverflowType.Ellipsis,
                wrapping:ej.datavisualization.Diagram.TextWrapping.NoWrap
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.style.textAlign`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            style: {
                textAlign: 'Justify',
                textOverflow : 'Wrap',
                textDecoration : 'LineThrough',
                textWrapping : 'WrapWithOverflow'
            }
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables or disables the visibility of the label</b></td>
<td>
<b>Property</b>:<i>`labels.visible`</i>
</br>
</br>
<code>
$("#diagram").ejDiagram({
    nodes: [{
        name: "node",
        width: 100,
        height: 100,
        offsetX: 100,
        offsetY: 100,
        labels: [
            {
                text: "Label",
                visible: false
            }
        ]
    }],
});
</code>
</td>
<td>
<b>Property</b>:<i>`annotations.visible`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    nodes: [{
        offsetX: 100,
        offsetY: 100,
        width: 100,
        height: 100,
        annotations: [{
            content: 'Annotation',
            visible : false
        }]
    }]
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Gets whether the label is currently being edited or not</b></td>
<td>
<b>Property</b>:<i>`labels.mode`</i>
</br>
</br>
<code>
var node = diagram.selectionList[0];
console.log(node.labels[0].mode);
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
</table>

## PageSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the size and appearance of diagram page</b></td>
<td>
<b>Property</b>:<i>`pageSettings.autoScrollBorder`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    pageSettings: {
        autoScrollBorder: { left: 50, top: 50, right: 50, bottom: 50 }
        }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets whether multiple pages can be created to fit all nodes and connectors</b></td>
<td>
<b>Property</b>:<i>`pageSettings.multiplePage`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    pageSettings: {
        multiplePage:false
        pageWidth: 800,
        pageHeight: 500,
        pageOrientation:ej.datavisualization.Diagram.PageOrientations.Landscape
        }
});
</code>
</td>
<td>
<b>Property</b>:<i>`pageSettings.multiplePage`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    pageSettings: {
        width: 800, height: 600, multiplePage: true,
        orientation:'Landscape'
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the background color of diagram pages</b></td>
<td>
<b>Property</b>:<i>`pageSettings.pageBackgroundColor`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    pageSettings: {
        pagebackgroundColor: "lightgrey",
        }
});
</code>
</td>
<td>
<b>Property</b>:<i>`pageSettings.background.color`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    pageSettings: {
    background: {
        color: 'red',
        source: 'Clayton.png',
        scale: 'Meet',
        align: 'XMidYMid'
    }
},
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the scrollable area of diagram. Applicable, if the scroll limit is “limited”</b></td>
<td>
<b>Property</b>:<i>`pageSettings.scrollableArea`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    pageSettings: {
        scrollableArea: { x:0, y:0, width:1000, height:1000}
        }
});
</code>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.scrollableArea`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        scrollableArea: new Rect(0, 0, 300, 300),
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the draggable region of diagram elements</b></td>
<td>
<b>Property</b>:<i>`pageSettings.boundaryConstraints`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    pageSettings: {
        boundaryConstraints: ej.datavisualization.Diagram.BoundaryConstraints.Diagram
        }
});
</code>
</td>
<td>
<b>Property</b>:<i>`pageSettings.boundaryConstraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    pageSettings: {
        width: 800, height: 600, boundaryConstraints: 'Diagram'
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## SymbolPalette

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the size and preview size of the node to add that to symbol palette</b></td>
<td>
<b>Property</b>:<i>`nodes.paletteItem`</i>
</br>
</br>
<code>
$("#symbolpalette").ejSymbolPalette({
    palettes: [{
        name: "Basic Shapes",
        expanded: true,
        items: [{
            name: "Rectangle",
            height: 40,
            width: 80,
            paletteItem: {
                previewWidth: 100,
                previewHeight: 100
            }
        }]
    }]
});
</code>
</td>
<td>
<b>Property</b>:<i>`palettes`</i>
</br>
</br>
<code>
export function getFlowShapes(): NodeModel[] {
    var flowShapes = [{
            id: 'Terminator',
            shape: {
                type: 'Flow',
                shape: 'Terminator'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Process',
            shape: {
                type: 'Flow',
                shape: 'Process'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Decision',
            shape: {
                type: 'Flow',
                shape: 'Decision'
            },
            style: {
                strokeWidth: 2
            }
        },
    ]
};
var palette = new ej.diagrams.SymbolPalette({
    expandMode: 'Multiple',
    palettes: [{
        id: 'flow',
        expanded: true,
        symbols: getFlowShapes(),
        title: 'Flow Shapes'
    }, ],
    width: '100%',
    height: '100%',
    symbolHeight: 50,
    symbolWidth: 50,
    symbolPreview: {
        height: 100,
        width: 100
    },
    enableSearch: true,
    symbolMargin: {
        left: 12,
        right: 12,
        top: 12,
        bottom: 12
    },
    getSymbolInfo: (symbol: NodeModel): SymbolInfo => {
        return {
            fit: true
        };
    }
});
palette.appendTo('#symbolpalette');
</code></td>
</tr>

<tr>
<td><b>Defines whether the symbol should be drawn at its actual size regardless of precedence factors or not</b></td>
<td>
<b>Property</b>:<i>`nodes.paletteItem.enableScale`</i>
</br>
</br>
<code>
$("#symbolpalette").ejSymbolPalette({
    palettes: [{
        name: "Basic Shapes",
        expanded: true,
        items: [{
            name: "Rectangle",
            height: 40,
            width: 80,
            paletteItem: {
                previewWidth: 100,
                previewHeight: 100,
                enableScale:false
            }
        }]
    }]
});
</code>
</td>
<td>
<b>Property</b>:<i>`palettes.fit`</i>
</br>
</br>
<code>
export function getFlowShapes(): NodeModel[] {
    var flowShapes = [{
            id: 'Terminator',
            shape: {
                type: 'Flow',
                shape: 'Terminator'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Process',
            shape: {
                type: 'Flow',
                shape: 'Process'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Decision',
            shape: {
                type: 'Flow',
                shape: 'Decision'
            },
            style: {
                strokeWidth: 2
            }
        },
    ]
};
var palette = new ej.diagrams.SymbolPalette({
    expandMode: 'Multiple',
    palettes: [{
        id: 'flow',
        expanded: true,
        symbols: getFlowShapes(),
        title: 'Flow Shapes'
    }, ],
    width: '100%',
    height: '100%',
    symbolHeight: 50,
    symbolWidth: 50,
    symbolPreview: {
        height: 100,
        width: 100
    },
    enableSearch: true,
    symbolMargin: {
        left: 12,
        right: 12,
        top: 12,
        bottom: 12
    },
    getSymbolInfo: (symbol: NodeModel): SymbolInfo => {
        return {
            fit: true
        };
    }
});
palette.appendTo('#symbolpalette');
</code></td>
</tr>

<tr>
<td><b>To display a name for nodes in the symbol palette</b></td>
<td>
<b>Property</b>:<i>`nodes.paletteItem.label`</i>
</br>
</br>
<code>
$("#symbolpalette").ejSymbolPalette({
    palettes: [{
        name: "Basic Shapes",
        expanded: true,
        items: [{
            name: "Rectangle",
            height: 40,
            width: 80,
            paletteItem: {
                previewWidth: 100,
                previewHeight: 100,
                label: "label",
                margin: { left: 4, right: 4, top: 4, bottom: 4 }
            }
        }]
    }]
});
</code>
</td>
<td>
<b>Property</b>:<i>`palettes.title`</i>
</br>
</br>
<code>
export function getFlowShapes(): NodeModel[] {
    var flowShapes = [{
            id: 'Terminator',
            shape: {
                type: 'Flow',
                shape: 'Terminator'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Process',
            shape: {
                type: 'Flow',
                shape: 'Process'
            },
            style: {
                strokeWidth: 2
            }
        },
        {
            id: 'Decision',
            shape: {
                type: 'Flow',
                shape: 'Decision'
            },
            style: {
                strokeWidth: 2
            }
        },
    ]
};
var palette = new ej.diagrams.SymbolPalette({
    expandMode: 'Multiple',
    palettes: [{
        id: 'flow',
        expanded: true,
        symbols: getFlowShapes(),
        title: 'Flow Shapes'
    }, ],
    width: '100%',
    height: '100%',
    symbolHeight: 50,
    symbolWidth: 50,
    symbolPreview: {
        height: 100,
        width: 100
    },
    enableSearch: true,
    symbolMargin: {
        left: 12,
        right: 12,
        top: 12,
        bottom: 12
    },
    getSymbolInfo: (symbol: NodeModel): SymbolInfo => {
        return {
            fit: true
        };
    }
});
palette.appendTo('#symbolpalette');
</code></td>
</tr>
</table>

## ScrollSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines the zoom value, zoom factor, scroll status and view port size of the diagram</b></td>
<td>
<b>Property</b>:<i>`scrollSettings.horizontalOffset`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    scrollSettings: {
        horizontalOffset: 300, verticalOffset: 300
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.horizontalOffset`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        horizontalOffset: 300, verticalOffset: 300
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Allows to read the view port width of the diagram</b></td>
<td>
<b>Property</b>:<i>`scrollSettings.viewPortWidth`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    scrollSettings: {
        viewPortWidth: 300, viewPortHeight: 300
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.viewPortWidth`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        viewPortWidth: 300, viewPortHeight: 300
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Allows to extend the scrollable region that is based on the scroll limit</b></td>
<td>
<b>Property</b>:<i>`scrollSettings.padding`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    scrollSettings: {
        padding: { left: 25, right: 25, top: 25, bottom: 25 }
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Allows to read the zoom value of diagram</b></td>
<td>
<b>Property</b>:<i>`scrollSettings.currentZoom`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    scrollSettings: {
        currentZoom: 0.2
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.currentZoom`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        currentZoom: 0.2,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Allows to read the maximum zoom value of scroller</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.maxZoom`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        maxZoom: 0.23
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Allows to read the maximum zoom value of scroller</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.autoScrollBorder`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        autoScrollBorder: { left: 25, right: 25, top: 25, bottom: 25 }
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables/Disables the autoscroll option</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.canAutoScroll`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        canAutoScroll: false,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the scrollable area of diagram</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`scrollSettings.scrollableArea`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    scrollSettings: {
        scrollableArea: new Rect(0, 0, 300, 300),
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## RulerSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Enables or disables both the horizontal and vertical ruler</b></td>
<td>
<b>Property</b>:<i>`rulerSettings.showRulers`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    rulerSettings: {
        showRulers: true,
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`rulerSettings.showRulers`</i>
</br>
</br>
<code>
var arrange = (args: IArrangeTickOptions) => {
    if (args.tickInterval % 10 == 0) {
        args.tickLength = 25;
        }
    }
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    rulerSettings: {
        showRulers: true,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables or disables both the horizontal and vertical ruler</b></td>
<td>
<b>Property</b>:<i>`rulerSettings.horizontalRuler`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    rulerSettings: {
        showRulers: true,
        horizontalRuler: {
            segmentWidth: 50, interval: 10,
            thickness: 50,
            length: 1000,
            markerColor: "pink",
            tickAlignment: ej.datavisualization.Diagram.TickAlignment.LeftOrTop,
            arrangeTick: function alignTick(args){ }
         },
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`rulerSettings.horizontalRuler`</i>
</br>
</br>
<code>
var arrange = (args: IArrangeTickOptions) => {
    if (args.tickInterval % 10 == 0) {
        args.tickLength = 25;
        }
    }
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    rulerSettings: {
        showRulers: true,
        horizontalRuler: {
            segmentWidth: 50,
            interval: 10,
            thickness: 20,
            markerColor: 'red',
            tickAlignment: 'LeftOrTop',
            arrangeTick: arrange,
            orientation: 'Horizontal',
            },
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Enables or disables both the horizontal and vertical ruler</b></td>
<td>
<b>Property</b>:<i>`rulerSettings.verticalRuler`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    rulerSettings: {
        showRulers: true,
        verticalRuler: {
            segmentWidth: 50, interval: 10,
            thickness: 50,
            length: 1000,
            markerColor: "pink",
            tickAlignment: ej.datavisualization.Diagram.TickAlignment.LeftOrTop,
            arrangeTick: function alignTick(args){ }
        }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>`rulerSettings.verticalRuler`</i>
</br>
</br>
<code>
var arrange = (args: IArrangeTickOptions) => {
    if (args.tickInterval % 10 == 0) {
        args.tickLength = 25;
        }
    }
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    rulerSettings: {
        showRulers: true,
        verticalRuler: {
            segmentWidth: 200,
            interval: 20,
            arrangeTick: arrange,
            thickness: 20,
            markerColor: 'red',
            tickAlignment: 'LeftOrTop',
            arrangeTick: arrange,
            orientation: 'Horizontal'
            }
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Updates the gridlines relative to the ruler ticks</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`rulerSettings.dynamicGrid`</i>
</br>
</br>
<code>
var arrange = (args: IArrangeTickOptions) => {
    if (args.tickInterval % 10 == 0) {
        args.tickLength = 25;
        }
    }
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    rulerSettings: {
        dynamicGrid: true,
        showRulers: true,
    },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## SnapSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Enables or disables snapping nodes/connectors to objects</b></td>
<td>
<b>Property</b>:<i>`snapSettings.enableSnapToObject`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    snapSettings: { enableSnapToObject: false }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines the appearance of horizontal gridlines</b></td>
<td>
<b>Property</b>:<i>`snapSettings.horizontalGridLines`</i>
</br>
</br>
<code>
var gridline = {
    lineColor :"blue",
    lineDashArray:"2,2",
    linesInterval: [1, 14, 0.5, 14.5 ],
    snapInterval : [5]
    };
$("#diagramcontent").ejDiagram({
    snapSettings: { horizontalGridLines: gridline}
    });
</code>
</td>
<td>
<b>Property</b>:<i>`snapSettings.horizontalGridlines`</i>
</br>
</br>
<code>
var snapSettings = {
    horizontalGridLines: {
        lineColor: 'black',
        lineDashArray: '1,1',
        lineIntervals: [0.95, 9.05, 0.2, 9.75],
        snapIntervals: [10]
        }
};
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    snapSettings: snapSettings
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the appearance of vertical gridlines</b></td>
<td>
<b>Property</b>:<i>`snapSettings.verticalGridLines`</i>
</br>
</br>
<code>
var gridline = {
    lineColor :"blue",
    lineDashArray:"2,2",
    linesInterval: [1, 14, 0.5, 14.5 ],
    snapInterval : [5]
    };
$("#diagramcontent").ejDiagram({
    snapSettings: { verticalGridLines: gridline}
    });
</code>
</td>
<td>
<b>Property</b>:<i>`snapSettings.verticalGridlines`</i>
</br>
</br>
<code>
var snapSettings = {
    verticalGridLines: {
        lineColor: 'black',
        lineDashArray: '1,1',
        lineIntervals: [0.95, 9.05, 0.2, 9.75],
        snapIntervals: [10]
        }
};
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    snapSettings: snapSettings
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the angle by which the object needs to be snapped</b></td>
<td>
<b>Property</b>:<i>`snapSettings.snapAngle`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({snapSettings: { snapAngle: 10} });
</code>
</td>
<td>
<b>Property</b>:<i>`snapSettings.snapAngle`</i>
</br>
</br>
<code>
var snapSettings = {
    snapAngle: 5,
};
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    snapSettings: snapSettings
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the minimum distance between the selected object and the nearest object</b></td>
<td>
<b>Property</b>:<i>`snapSettings.snapObjectDistance`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    snapSettings: { snapObjectDistance: 5 }
});
</code>
</td>
<td>
<b>Property</b>:<i>`snapSettings.snapObjectDistance`</i>
</br>
</br>
<code>
var snapSettings = {
    snapObjectDistance: 5,
};
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    snapSettings: snapSettings
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines and sets the snapConstraints</b></td>
<td>
<b>Property</b>:<i>`snapSettings.snapConstraints`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    snapSettings: { snapConstraints : ej.datavisualization.Diagram.SnapConstraints.ShowLines }
});
</code>
</td>
<td>
<b>Property</b>:<i>`snapSettings.constraints`</i>
</br>
</br>
<code>
var snapSettings = {
    constraints: SnapConstraints.ShowLines,
};
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    snapSettings: snapSettings
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## ZoomFactor

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Sets the factor by which we can zoom in or zoom out</b></td>
<td>
<b>Property</b>:<i>`zoomFactor`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({zoomFactor: 1});
</code>
</td>
<td>
<b>Property</b>:<i>`zoomFactor`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
});
diagram.appendTo('#diagram');
var zoomin = { type: 'ZoomIn', zoomFactor: 0.5 };
diagram.zoomTo(zoomin);
</code></td>
</tr>
</table>

## Tool

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Enables/Disables the interactive behaviors of diagram</b></td>
<td>
<b>Property</b>:<i>`tool`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({tool: ej.datavisualization.Diagram.Tool.ZoomPan});
</code>
</td>
<td>
<b>Property</b>:<i>`tool`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
});
diagram.appendTo('#diagram');
diagram.tool = DiagramTools.ZoomPan;
</code></td>
</tr>
</table>

## ShowTooltip

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Enables or disables tooltip of diagram</b></td>
<td>
<b>Property</b>:<i>`showTooltip`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({showTooltip: true});
</code>
</td>
<td>
<b>Property</b>:<i>`constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## SelectedItems

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>A read only collection of the selected items</b></td>
<td>
<b>Property</b>:<i>`selectedItems.children`</i>
</br>
</br>
<code>
var diagram = $("#diagramcontent").ejDiagram("instance");
for(var i =0; i< diagram.model.selectedItems.children; i++){
    //Do your actions here
}
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Controls the visibility of selector</b></td>
<td>
<b>Property</b>:<i>`selectedItems.constraints`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
     selectedItems: { constraints: ej.datavisualization.Diagram.SelectorConstraints.UserHandles }
});
</code>
</td>
<td>
<b>Property</b>:<i>`selectedItems.constraints`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    selectedItems: { constraints: SelectorConstraints.UserHandles },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines a method that dynamically enables/ disables the interaction with multiple selection</b></td>
<td>
<b>Property</b>:<i>`selectedItems.getConstraints`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
selectedItems: {
    getConstraints: function() {
        return ej.datavisualization.Diagram.NodeConstraints.Drag |
        ej.datavisualization.Diagram.NodeConstraints.Resize
        }
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the height of the selected items</b></td>
<td>
<b>Property</b>:<i>`selectedItems.height`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
     selectedItems: {
        height:100, width: 100,
        offsetX:100, offsetY: 100,
        rotateAngle: 90,
      }
});
</code>
</td>
<td>
<b>Property</b>:<i>`selectedItems.height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    selectedItems: {
        height:100, width: 100,
        offsetX:100, offsetY: 100,
        rotateAngle: 90 },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the angle to rotate the selected items</b></td>
<td>
<b>Property</b>:<i>`selectedItems.tooltip`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
     selectedItems: {
        tooltip : { alignment:{ vertical:"top" } }
      }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>A collection of frequently used commands that will be added around the selector</b></td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles`</i>
</br>
</br>
<code>
var userHandle= [];
var cloneHandle = ej.datavisualization.Diagram.UserHandle();
userHandle.push(cloneHandle);
$("#diagramcontent").ejDiagram({
    selectedItems: {
        userHandles:userHandle
        }
    });
</code>
</td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles`</i>
</br>
</br>
<code>
var handle = [{
    name: 'handle1', pathData: 'M 60.3,18 H 27.5 c -3,0-5.5,2.4-5.5,5.5 v 38.2 h 5.5 V 23.5 h 32.7 V 18 z M 68.5,28.9 h -30 c -3,0-5.5,2.4-5.5,5.5 v 38.2 c 0,3,2.4,5.5,5.5,5.5 h 30 c 3,0,5.5-2.4,5.5-5.5 V 34.4 C 73.9,31.4,71.5,28.9,68.5,28.9 z M 68.5,72.5 h -30 V 34.4 h 30 V 72.5 z'
    , visible: true, backgroundColor: 'black', offset: 0, side: 'Bottom', margin: { top: 0, bottom: 0, left: 0, right: 0 },
    pathColor: 'white'
}];
var diagram = new ej.diagrams.Diagram({
    selectedItems: {
        constraints: SelectorConstraints.UserHandles,
        userHandles: handle
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the user handle</b></td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles.horizontalAlignment`</i>
</br>
</br>
<code>
var userHandle = [];
var cloneHandle = ej.datavisualization.Diagram.UserHandle();
cloneHandle = {name : "cloneHandle",

pathData : "M 4.6350084,4.8909971 L 4.6350084,9.3649971 9.5480137,9.3649971 9.5480137,4.8909971 z M 3.0000062,2.8189973 L 11.184016,2.8189973 11.184016,10.999997 3.0000062,10.999997 z M 0,0 L 7.3649998,0 7.3649998,1.4020001 1.4029988,1.4020001 1.4029988,8.0660002 0,8.0660002 0,1.4020001 0,0.70300276 z",

visible : "true",

backgroundColor : "#4D4D4D",

offset : ej.datavisualization.Diagram.point(0, 0),

position :" middleleft"

margin : { left: 5 },

pathColor : "white",

horizontalAlignment : ej.datavisualization.Diagram.HorizontalAlignment.Right,
verticalAlignment : ej.datavisualization.Diagram.VerticalAlignment.Top,

borderColor : "red",
borderWidth : 3,

size : 20};

userHandle.push(cloneHandle);

$("#diagramcontent").ejDiagram({
     selectedItems: {
        userHandles:userHandle
        }
});
</code>
</td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles.horizontalAlignment`</i>
</br>
</br>
<code>
var handle = [{
    name: 'handle1',
    pathData: 'M 60.3,18 H 27.5 c -3,0-5.5,2.4-5.5,5.5 v 38.2 h 5.5 V 23.5 h 32.7 V 18 z M 68.5,28.9 h -30 c -3,0-5.5,2.4-5.5,5.5 v 38.2 c 0,3,2.4,5.5,5.5,5.5 h 30 c 3,0,5.5-2.4,5.5-5.5 V 34.4 C 73.9,31.4,71.5,28.9,68.5,28.9 z M 68.5,72.5 h -30 V 34.4 h 30 V 72.5 z',
    visible: true,
    backgroundColor: 'black',
    offset: 0,
    side: 'Bottom',
    margin: { top: 0, bottom: 0, left: 0, right: 0 },
    pathColor: 'white',
    horizontalAlignment: 'Center',
    verticalAlignment: 'Center',
    borderColor: 'red',
    borderWidth: 3,
    size: 30
}];
var diagram = new ej.diagrams.Diagram({
    selectedItems: {
        constraints: SelectorConstraints.UserHandles,
        userHandles: handle
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the interactive behaviors of the user handle
</b></td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles.tool`</i>
</br>
</br>
<code>
var CloneTool = (function(base) {
    ej.datavisualization.Diagram.extend(CloneTool, base);

    function CloneTool(name) {
        base.call(this, name);
        this.singleAction = true;
        this.clonedNodes = [];
        this.cursor = "pointer";
    }
    CloneTool.prototype.mouseup = function(evt) {
        this.diagram.copy();
        this.diagram.paste();
    }
}
return CloneTool;
});
(ej.datavisualization.Diagram.ToolBase);
var userHandle = [];
var cloneHandle = ej.datavisualization.Diagram.UserHandle();
cloneHandle.name = "cloneHandle";

cloneHandle.pathData = "M 4.6350084,4.8909971 L 4.6350084,9.3649971 9.5480137,9.3649971 9.5480137,4.8909971 z M 3.0000062,2.8189973 L 11.184016,2.8189973 11.184016,10.999997 3.0000062,10.999997 z M 0,0 L 7.3649998,0 7.3649998,1.4020001 1.4029988,1.4020001 1.4029988,8.0660002 0,8.0660002 0,1.4020001 0,0.70300276 z";

cloneHandle.tool =  new CloneTool(cloneHandle.name);;

userHandle.push(cloneHandle);

$("#diagramcontent").ejDiagram({
     selectedItems: {
        userHandles: userHandle
        }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Defines whether the user handle should be added, when more than one element is selected
</b></td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles.enableMultiSelection`</i>
</br>
</br>
<code>
var userHandle = [];
var cloneHandle = ej.datavisualization.Diagram.UserHandle();
cloneHandle.name = "cloneHandle";
cloneHandle.enableMultiSelection = true;

userHandle.push(cloneHandle);

$("#diagramcontent").ejDiagram({
     selectedItems: {
        userHandles: userHandle
        }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the horizontal alignment of the user handle</b></td>
<td>
<b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`selectedItems.userHandles.displacement`</i>
</br>
</br>
<code>
var handle = [{
    name: 'handle1',
    pathData: 'M 60.3,18 H 27.5 c -3,0-5.5,2.4-5.5,5.5 v 38.2 h 5.5 V 23.5 h 32.7 V 18 z M 68.5,28.9 h -30 c -3,0-5.5,2.4-5.5,5.5 v 38.2 c 0,3,2.4,5.5,5.5,5.5 h 30 c 3,0,5.5-2.4,5.5-5.5 V 34.4 C 73.9,31.4,71.5,28.9,68.5,28.9 z M 68.5,72.5 h -30 V 34.4 h 30 V 72.5 z',
    displacement: 30
}];
var diagram = new ej.diagrams.Diagram({
    selectedItems: {
        constraints: SelectorConstraints.UserHandles,
        userHandles: handle
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>

## SerializationSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Defines whether the default diagram properties can be serialized or not</b></td>
<td>
<b>Property</b>:<i>`serializationSettings.preventDefaultValues`</i>
</br>
</br>
<code>
$("#diagramcontent").ejDiagram({
    serializationSettings: {
        preventDefaultValues: true
    }
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>
</table>

## Tooltip

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td style="width: 20%;"><b>Behaviour</b></td>
<td style="width: 40%;"><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>An object that defines the description, appearance and alignments of tooltip</b></td>
<td>
<b>Property</b>:<i>`tooltip`</i>
</br>
</br>
<code>
<script type="text/x-jsrender" id="mouseovertooltip">
   <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;">  </span>
   </div>
</script>
$("#diagramcontent").ejDiagram({
    tooltip: {
        templateId: "mouseovertooltip",
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Mouse,
    },
    nodes: [{
        name: "elizabeth",
        width: 70,
        height: 40,
        offsetX: 100,
        offsetY: 100,
        Designation: "Managing Director"
    }]
});
</code>
</td>
<td>
<b>Property</b>:<i>`tooltip`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        content: 'Diagram',
        position: 'TopLeft',
        relativeMode: 'Object',
        animation: {
            open: { effect: 'FadeZoomIn', delay: 0 },
            close: { effect: 'FadeZoomOut', delay: 0 }
            }
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the alignment of tooltip</b></td>
<td>
<b>Property</b>:<i>`tooltip.alignment`</i>
</br>
</br>
<code>
<script type="text/x-jsrender" id="mouseovertooltip">
   <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;">  </span>
   </div>
</script>
$("#diagramcontent").ejDiagram({
    tooltip: {
        templateId: "mouseovertooltip",
        alignment: {
            horizontal: "center",
            vertical: "bottom"
        },
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Mouse,
    },
    nodes: [{
        name: "elizabeth",
        width: 70,
        height: 40,
        offsetX: 100,
        offsetY: 100,
        Designation: "Managing Director"
    }]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Sets the margin of the tooltip</b></td>
<td>
<b>Property</b>:<i>`tooltip.margin`</i>
</br>
</br>
<code>
<script type="text/x-jsrender" id="mouseovertooltip">
   <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;">  </span>
   </div>
</script>
$("#diagramcontent").ejDiagram({
    tooltip: {
        templateId: "mouseovertooltip",
        alignment: {
            horizontal: "center",
            vertical: "bottom"
        },
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Mouse,
        margin : { left: 5, right: 5, top: 5, bottom: 5 }
    },
    nodes: [{
        name: "elizabeth",
        width: 70,
        height: 40,
        offsetX: 100,
        offsetY: 100,
        Designation: "Managing Director"
    }]
});
</code>
</td>
<td>
<b>Not applicable</b></td>
</tr>

<tr>
<td><b>Sets the svg/html template to be bound with tooltip</b></td>
<td>
<b>Property</b>:<i>`tooltip.templateId`</i>
</br>
</br>
<code>
<script type="text/x-jsrender" id="mouseovertooltip">
   <div style="background-color: #F08080; color: white; white-space: nowrap; height: 20px">
        <span style="padding: 5px;">  </span>
   </div>
</script>
$("#diagramcontent").ejDiagram({
    tooltip: {
        templateId: "mouseovertooltip",
        alignment: {
            horizontal: "center",
            vertical: "bottom"
        },
        relativeMode: ej.datavisualization.Diagram.RelativeMode.Mouse,
        margin : { left: 5, right: 5, top: 5, bottom: 5 }
    },
    nodes: [{
        name: "elizabeth",
        width: 70,
        height: 40,
        offsetX: 100,
        offsetY: 100,
        Designation: "Managing Director"
    }]
});
</code>
</td>
<td>
<b>Property</b>:<i>`tooltip.content`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        content: 'Diagram',
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines if the Tooltip has tip pointer or not</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`tooltip.showTipPointer`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        content: 'Diagram',
        showTipPointer: true,
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Defines the position of the Tooltip</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`tooltip.position`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        content: 'Diagram',
        position: 'TopLeft',
        relativeMode: 'Object',
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Allows to set the same or different animation option for the Tooltip, when it is opened or closed</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`tooltip.animation`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        content: 'Diagram',
        position: 'TopLeft',
        relativeMode: 'Object',
        animation: {
            open: { effect: 'FadeZoomIn', delay: 0 },
            close: { effect: 'FadeZoomOut', delay: 0 }
            }
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the width of the tooltip</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`tooltip.width`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        width: 100,
        content: 'Diagram',
        position: 'TopLeft',
        relativeMode: 'Object'
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>

<tr>
<td><b>Sets the height of the Tooltip</b></td>
<td><b>Not applicable</b>
</td>
<td>
<b>Property</b>:<i>`tooltip.height`</i>
</br>
</br>
<code>
var diagram = new ej.diagrams.Diagram({
    width: '100%', height: '600px',
    constraints: DiagramConstraints.Default | DiagramConstraints.Tooltip,
    tooltip: {
        height: 100,
        content: 'Diagram',
        position: 'TopLeft',
        relativeMode: 'Object',
        },
});
diagram.appendTo('#diagram');
</code></td>
</tr>
</table>