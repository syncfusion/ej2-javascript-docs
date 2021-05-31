# Drag and Drop

Drag and Drop is supported through two libraries. Those are [`Draggable`](../api/base/draggable) and [`Droppable`](../api/base/droppable). Draggable makes DOM to be dragged using mouse or touch gestures and Droppable mark required DOM as droppable zone.

## Initializing draggable

You can make any element draggable by passing the element to Draggable constructor. Refer the following code snippet to enable draggable for DOM element.

 {% tab template="common/draggable-default", es5Template="draggable-default-template" %}

 ```javascript
 var dragElement = document.getElementById('element1');
 var draggable = new ej.base.Draggable(dragElement,{clone: false});

 document.getElementById('loader').style.display = "none";
 document.getElementById('container').style.visibility = "visible";
 ```

 {% endtab %}

## Creating droppable zone

You can convert any DOM element as a droppable zone, which accepts the draggable elements. Refer the following code snippet to enable droppable zone.

{% tab template="common/droppable-default", es5Template="droppable-default-template" %}

 ```javascript
 var droppable = new ej.base.Droppable(document.getElementById('droppable'));

 document.getElementById('loader').style.display = "none";
 document.getElementById('container').style.visibility = "visible";
 ```

 {% endtab %}

## Defining drop action

To define drop action set [`drop`](../../api/base/droppable#drop) callback function during droppable object creation. You can get details of dropped element through dropped element property in event argument. Refer the following code snippet to use basic drag and drop action.

{% tab template="common/drag-drop-action", es5Template="drag-drop-template" %}

 ```javascript
 var draggable = new ej.base.Draggable(document.getElementById('element1'), {
    clone: false
 });

 var droppable = new ej.base.Droppable(document.getElementById('droppable'), {
    drop: (function (e) {
        e.droppedElement.querySelector('.drag-text').textContent = 'Dropped';
    })
 });

 document.getElementById('loader').style.display = "none";
 document.getElementById('container').style.visibility = "visible";
 ```

 {% endtab %}

## See Also

[Define handle element for Draggable](../api/base/draggable#handle)<br/>
[Restricting Draggable within conainer](../api/base/draggable#dragarea)<br>
[Visual feedback of draggable element](../api/base/draggable#clone)<br>
[Accepting specific drag element in droppable](../api/base/droppable#accept)