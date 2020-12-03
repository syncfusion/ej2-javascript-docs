# Tooltip open or display modes

The open mode property of tooltip can be defined on a target that is hovering, focusing, or clicking.
Tooltip component have the following types of open mode:

* Auto
* Hover
* Click
* Focus
* Custom

## Auto

Tooltip appears when you hover over the target or when the target element receives the focus.

## Hover

Tooltip appears when you hover over the target.

## Click

Tooltip appears when you click a target element.

## Focus

Tooltip appears when you focus (say through tab key) on a target element.

## Custom

Tooltip is not triggered by any default action. So, bind your own events and use either open or close public methods.

{% tab template="tooltip/open-property", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="open-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';

//Render button components

let tooltiphover: Button = new Button({ cssClass: 'e-outline', isPrimary: true });
tooltiphover.appendTo('#tooltiphover');

let tooltipclick: Button = new Button({ cssClass: 'e-outline', isPrimary: true });
tooltipclick.appendTo('#tooltipclick');

let tooltipcustom: Button = new Button({ cssClass: 'e-outline', isPrimary: true });
tooltipcustom.appendTo('#tooltipcustom');

let Mode: Button = new Button({ cssClass: 'e-outline', isPrimary: true });
Mode.appendTo('#Mode');

let open: Button = new Button({ cssClass: 'e-outline', isPrimary: true });
open.appendTo('#openMode');

//Render tooltip component

let hoverTooltip: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    opensOn: 'Hover',
    content: 'Tooltip from hover'
});
hoverTooltip.appendTo('#tooltiphover');

let clickTooltip: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    opensOn: 'Click',
    content: 'Tooltip from click'
});
clickTooltip.appendTo('#tooltipclick');

let focusTooltip: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    opensOn: 'Focus',
    content: 'Tooltip from focus'
});
focusTooltip.appendTo('#focus');

let customTooltip: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    opensOn: 'Custom',
    content: 'Tooltip from custom mode'
});
customTooltip.appendTo('#tooltipcustom');

let openMode: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    openDelay: 1000,
    closeDelay: 1000,
    position: 'BottomCenter',
    content: 'Opens and closes Tooltip with delay of <i>1000 milliseconds</i>'
});
openMode.appendTo('#openMode');

let mode: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    content: 'Click close icon to close me',
    position: 'BottomCenter',
    isSticky: true
});
mode.appendTo('#Mode');

document.getElementById('tooltipcustom').addEventListener("dblclick", function () {
    if (this.getAttribute("data-tooltip-id")) {
        customTooltip.close();
    } else {
        customTooltip.open(this);
    }
});

```

{% endtab %}