---
title: "Animation For Tooltip"
component: "Tooltip"
description: "TypeScript tooltip component supports various animation effects while showing or hiding the tooltip."
---

# Animation

To animate the Tooltip, a set of specific animation effects are available, and it can be controlled using the `animation` property.
 The animation property also allows you to set delay, duration, and various other effects of your choice.

[`AnimationModel`](../api/tooltip/tooltipAnimationSettings) is derived from base to apply the chosen animation effect, duration, etc. on Tooltips.

By default, Tooltip entrance occurs over 150 ms using the `ease-out` timing function. It exits also at 150 ms,
but uses `ease-in` timing function.

{% tab template="tooltip/animation/default-animation", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="default-animation-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';

let tooltip: Tooltip = new Tooltip({
    content: 'Tooltip content',
    animation: {
        open: { effect: 'ZoomIn', duration: 1000, delay: 0 },
        close: { effect: 'ZoomOut', duration: 500, delay: 0 }
    }
});
tooltip.appendTo('#target');

```

{% endtab %}

The default animation effect for the Tooltip is set to `FadeIn` for its open action, and `FadeOut` for its close action.
The default `duration` is set to 150 ms and `delay` is set to 0.

## Animation effects

The animation effects that are applicable to Tooltips are:

* FadeIn
* FadeOut
* FadeZoomIn
* FadeZoomOut
* FlipXDownIn
* FlipXDownOut
* FlipXUpIn
* FlipXUpOut
* FlipYLeftIn
* FlipYLeftOut
* FlipYRightIn
* FlipYRightOut
* ZoomIn
* ZoomOut
* None

When the `effect` is specified as `none`, no effect will be applied to the Tooltip, and animation is considered to be set to `off`.

> Some of the above animation effects suits the Tooltip better when its tip pointer is hidden.
> This can be achieved by setting the `showTipPointer` to false.

## Animating via open/close methods

Animations can also be applied on Tooltips dynamically through `open` and `close` methods. These methods accept the animation model as an
 optional parameter. If you pass `TooltipAnimationSettings`, animation takes this model; otherwise, it takes the values from the
  `animation` property. It is also possible to pass different animations for Tooltips on each target.

Refer to the code snippet below to apply animations using public methods.

{% tab template="tooltip/animation/animation-effects", isDefaultActive=true, sourceFiles="index.ts,index.html", es5Template="animation-effects-template" %}

```typescript
import { Tooltip, TooltipAnimationSettings } from '@syncfusion/ej2-popups';

let tooltip: Tooltip = new Tooltip({
    content: 'Tooltip content',
    opensOn: 'custom'
});
tooltip.appendTo('#target');


document.getElementById('target').addEventListener("click", function () {
    if (this.getAttribute("data-tooltip-id")) {
        let closeAnimation: TooltipAnimationSettings = { effect: 'FadeOut', duration: 1000 }
        tooltip.close(closeAnimation);
    } else {
        let openAnimation: TooltipAnimationSettings = { effect: 'FadeIn', duration: 1000 }
        tooltip.open(this, openAnimation);
    }
});

```

{% endtab %}

## Apply transition

The transition effect can be applied on Tooltips by using the `beforeRender` event as given in the
 following work-around code example.

{% tab template="tooltip/transition", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="transition-template" %}

```typescript
import { Tooltip, TooltipEventArgs } from '@syncfusion/ej2-popups';
let tooltip: Tooltip = new Tooltip({
    target: '.circletool',
    closeDelay: 1000,
    animation: { open: { effect: 'ZoomIn', duration: 500 }, close: { effect: 'ZoomOut', duration: 500 } },
    beforeRender: onBeforeRender,
    afterClose: onAfterClose
});
function onBeforeRender(args: TooltipEventArgs): void {
    if (args.element) {
        // here prevent animation while apply transition
        this.animation = { open: { effect: 'None' } };
        args.element.style.display = 'block';
        args.element.style.transitionProperty = 'left,top';
        args.element.style.transitionDuration = '1000ms';
    }
}
function onAfterClose(args: TooltipEventArgs): void {
    // restore the animation effects
    this.animation = { open: { effect: 'ZoomIn', duration: 500 }, close: { effect: 'ZoomOut', duration: 500 } };
}
tooltip.appendTo('#box');

```

{% endtab %}
