---
title: "Scroll Settings"
component: "Diagram"
description: "Scroll settings allow you to scroll the diagram by using the vertical and horizontal scroll bars."
---

# Scroll Settings

The diagram can be scrolled by using the vertical and horizontal scrollbars. In addition to the scrollbars,mousewheel can be used to scroll the diagram.
Diagram’s [`scrollSettings`](../api/diagram) enable you to read the current scroll status, view port size, current zoom, and zoom factor. It also allows you to scroll the diagram programmatically.

## Get current scroll status

Scroll settings allow you to read the scroll status, [`viewPortWidth`](../api/diagram/scrollSettings), [`viewPortHeight`](../api/diagram/scrollSettings), and [`currentZoom`](../api/diagram/scrollSettings) with a set of properties. To explore those properties, see [`Scroll Settings`](../api/diagram/scrollSettings).

## Define scroll status

Diagram allows you to pan the diagram before loading, so that any desired region of a large diagram is made to view. You can programmatically pan the diagram with the [`horizontalOffset`](../api/diagram/scrollSettings) and [`verticalOffset`](../api/diagram/scrollSettings) properties of scroll settings. The following code illustrates how to set pan the diagram programmatically.

In the following example, the vertical scroll bar is scrolled down by 50 px and horizontal scroll bar is scrolled to right by 100 px.

{% tab template= "diagram/scrollSettings", es5Template="scroll" %}

```typescript
import {
    Diagram,BasicShapeModel,NodeModel,DiagramTools
} from '@syncfusion/ej2-diagrams';
//Sets scroll status
let diagram: Diagram = new Diagram({
    width: '100%', height: 700,scrollSettings: {
    horizontalOffset: 100,verticalOffset: 50
    }
});
diagram.appendTo('#element');

```

{% endtab %}

## Update scroll status

You can programmatically change the scroll offsets at runtime by using the client-side method update. The following code illustrates how to change the scroll offsets and zoom factor at runtime.

{% tab template= "diagram/scrollSettings", es5Template="updateScroll" %}

```typescript
import {
    Diagram,BasicShapeModel,NodeModel,DiagramTools
} from '@syncfusion/ej2-diagrams';
let diagram: Diagram = new Diagram({
    width: '100%', height: 700
});
diagram.appendTo('#element');

//Updates scroll settings
diagram.scrollSettings.horizontalOffset=200;
diagram.scrollSettings.verticalOffset=30
diagram.dataBind();

```

{% endtab %}

## AutoScroll

Autoscroll feature automatically scrolls the diagram, whenever the node or connector is moved beyond the boundary of the diagram. So that, it is always visible during dragging, resizing, and multiple selection operations. Autoscroll is automatically triggered when any one of the following is done towards the edges of the diagram.

* Node dragging, resizing
* Connection editing
* Rubber band selection
* Label dragging

The diagram client-side event [`ScrollChange`](../api/diagram) gets triggered when the autoscroll (scrollbars) is changed and you can do your own customization in this event.

The autoscroll behavior in your diagram can be enabled/disabled by using the [`canAutoScroll`](../api/diagram/scrollSettings) property of the diagram.

## Autoscroll border

The autoscroll border is used to specify the maximum distance between the object and diagram edge to trigger autoscroll. The default value is set as 15 for all sides (left, right, top, and bottom) and it can be changed by using the [`autoScrollBorder`](../api/diagram/scrollSettings) property of page settings. The following code example illustrates how to set autoscroll border.

{% tab template= "diagram/scrollSettings", es5Template="autoScroll" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
let nodes: NodeModel[] = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    // set the autoScrollBorder
    scrollSettings:{autoScrollBorder:{left:100,right:100,top:100,bottom:100}},
    getNodeDefaults: (node: NodeModel) => {
        node.height =  100;
        node.width =  100;
        node.style.fill =  '#6BA5D7';
        node.style.strokeColor =  'white';
        return  node;
    }
});

diagram.appendTo('#element');

```

{% endtab %}

## Scroll limit

The scroll limit allows you to define the scrollable region of the diagram. It includes the following options:

* Allows to scroll in all directions without any restriction.
* Allows to scroll within the diagram content.
* Allows to scroll within the specified scrollable area.
* The [`scrollLimit`](../api/diagram/scrollSettings) property of scroll settings helps to limit the scrolling.

The scrollSettings [`scrollableArea`](../api/diagram/scrollSettings) allow to extend the scrollable region that is based on the scroll limit.
The following code example illustrates how to specify the scroll limit.

{% tab template= "diagram/scrollSettings", es5Template="scrollLimit" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
let nodes: NodeModel[] = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    // set the autoScrollBorder
    scrollSettings:{
    //Sets the scroll limit
    scrollLimit: 'infinity'
    },
    getNodeDefaults: (node: NodeModel) => {
        node.height =  100;
        node.width =  100;
        node.style.fill =  '#6BA5D7';
        node.style.strokeColor =  'white';
        return  node;
    }
});

diagram.appendTo('#element');

```

{% endtab %}

## Scroll Padding

The [`padding`](../api/diagram/scrollSettings) property of scroll settings allows you to extend the scrollable region that is based on the scroll limit.

The following code example illustrates how to set scroll padding to diagram region.

{% tab template= "diagram/scrollSettings", es5Template="scrollPadding" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
let nodes: NodeModel[] = [{
    id: 'Start',
    width: 100, height: 100,
    offsetX: 350, offsetY: 350,
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    scrollSettings: {
      //Sets the scroll padding
        padding: { right: 50, bottom: 50 }
        }
    },
});

diagram.appendTo('#element');

```

{% endtab %}

## Scrollable Area

Scrolling beyond any particular rectangular area can be restricted by using the [`scrollableArea`](../api/diagram/scrollSettings) property of scroll settings. To restrict scrolling beyond any custom region, set the [`scrollLimit`](../api/diagram/scrollSettings) as “limited”. The following code example illustrates how to customize scrollable area.

{% tab template= "diagram/scrollSettings", es5Template="scrollArea" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel
} from '@syncfusion/ej2-diagrams';
let nodes: NodeModel[] = [{
    id: 'Start',
    width: 140,
    height: 50,
    offsetX: 300,
    offsetY: 50,
    annotations: [{
        id: 'label1',
        content: 'Start'
    }],
    shape: {
        type: 'Flow',
        shape: 'Terminator'
    }
}];

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    nodes: nodes,
    scrollSettings:{
    //Sets the scroll limit
    scrollLimit: 'infinity',
    //Sets the scrollable Area
    scrollableArea: {
            x: 0,
            y: 0,
            width: 500,
            height: 500
        }

    },
    getNodeDefaults: (node: NodeModel) => {
        node.height =  100;
        node.width =  100;
        node.style.fill =  '#6BA5D7';
        node.style.strokeColor =  'white';
        return  node;
    }
});

diagram.appendTo('#element');

```

{% endtab %}

## UpdateViewport

The [`updateViewPort`](../api/diagram) method is used to update the diagram page and view size at runtime.