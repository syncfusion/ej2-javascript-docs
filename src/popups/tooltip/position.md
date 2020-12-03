---
title: "Tooltip Position"
component: "Tooltip"
description: "TypeScript tooltip can be displayed in 12 (twelve) different positions of target element that automatically collide based on view port."
---

# Tooltip Positioning

Tooltips can be attached to 12 static locations around the target.
On initializing the Tooltip, you can set the position property with any one of the following values:

* `TopLeft`
* `TopCenter`
* `TopRight`
* `BottomLeft`
* `BottomCenter`
* `BottomRight`
* `LeftTop`
* `LeftCenter`
* `LeftBottom`
* `RightTop`
* `RightCenter`
* `RightBottom`

> By default, Tooltip is placed at the `TopCenter` of the target element.

{% tab template="tooltip/position/default", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="position-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Button } from '@syncfusion/ej2-buttons';

let button: Button = new Button({content: 'Show Tooltip'});
button.appendTo('#tooltip');

let tooltip: Tooltip = new Tooltip({
  position: 'TopCenter',
  content: 'Tooltip Content'
});
tooltip.appendTo('#tooltip');

let dropDownListObject: DropDownList = new DropDownList({
  change: dropChange
});
dropDownListObject.appendTo('#positions');

function dropChange() {
  tooltip.close();
  tooltip.position = this.value;
}

```

{% endtab %}

## Tip pointer positioning

The Tooltip pointer can be attached or detached from the Tooltip by using the `showTipPointer` property.
Pointer positions can be adjusted using the `tipPointerPosition` property that can be assigned to one of the following values:

* `Auto`
* `Start`
* `Middle`
* `End`

The following code example illustrates how to set the pointer to the start position of the Tooltip.

{% tab template="tooltip/position/tip-position", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="tip-position-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';

let button: Button = new Button({content: 'Show Tooltip'});
button.appendTo('#target');
let tooltip: Tooltip = new Tooltip({
    tipPointerPosition: "Start"
});
tooltip.appendTo('#target');
```

{% endtab %}

By default, tip pointers are auto adjusted so that the arrow does not point outside the target element.

## Dynamic positioning

The Tooltip and its tip pointer can be positioned dynamically based on the target's location. This can be achieved by using the `refresh`
 method, which auto adjusts the Tooltip over the target.

{% tab template="tooltip/position/dynamic-position", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="dynamic-position-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Draggable } from '@syncfusion/ej2-base';
let tooltip: Tooltip;
tooltip = new Tooltip({
    content: 'Drag me !!!',
    target: '#demoSmart',
    animation: { open: { effect: 'None' }, close: { effect: 'None' } }
}, '#targetContainer');
let ele: HTMLElement = document.getElementById('demoSmart');
let drag: Draggable = new Draggable(ele, {
    clone: false,
    dragArea: '#targetContainer',
    drag: (args: any) => {
        tooltip.refresh(args.element);
    },
    dragStart: (args: any) => {
        tooltip.open(args.element);
    },
    dragStop: (args: any) => {
        tooltip.close();
    }
});

```

{% endtab %}

## Mouse trailing

Tooltips can be positioned relative to the mouse pointer. This behavior can be enabled or disabled by using the `mouseTrail` property.
 By default, it is set to `false`.

{% tab template="tooltip/position/mouse-trail", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="mouse-trail-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
let tooltip: Tooltip = new Tooltip({
    mouseTrail: true,
    content: 'Tooltip content'
});
tooltip.appendTo('#target');

```

{% endtab %}

> When mouse trailing option is enabled, the tip pointer position gets auto adjusted based on the target, and
> other position values like start, end, and middle are not applied (to prevent the pointer from moving out of target).

## Setting offset values

Offset values are set to specify the distance between the target and tooltip element.
`offsetX` and `offsetY` properties are used to specify the offset left and top values.

* `offsetX` specifies the distance between the target and Tooltip element in X axis.
* `offsetY` specifies the distance between the target and Tooltip element in Y axis.

The following code example illustrates how to set offset values.

{% tab template="tooltip/position/offset-value", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="offset-value-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
let tooltip: Tooltip = new Tooltip({
    offsetX: 30,
    offsetY: 30,
    mouseTrail: true,
    showTipPointer: false,
    content: 'Tooltip content'
});
tooltip.appendTo('#target');

```

{% endtab %}

> By default, collision is handled automatically and therefore when collision is detected the Tooltip fits horizontally and flips vertically.
