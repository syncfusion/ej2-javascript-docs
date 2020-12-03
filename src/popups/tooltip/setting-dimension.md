---
title: "Tooltip Position"
component: "Tooltip"
description: "TypeScript tooltip component’s dimension can either be assigned auto height and width values or specific pixel values."
---

# Setting Dimension

## Height and width

The Tooltip can either be assigned auto height and width values or specific pixel values. The `width` and `height` properties are used to
 set the outer dimension of the Tooltip element. The default value for both the properties is `auto`.
  It also accepts string and number values in pixels.

The following sample explains how to set dimensions for the Tooltip.

{% tab template="tooltip/dimensions/height-width", isDefaultActive=true, sourceFiles="index.ts,index.html", es5Template="height-width-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';

let tooltip: Tooltip = new Tooltip({
    width: '180px',
    height: '40px',
    content: 'This tooltip has 180px width and 40px height'
});
tooltip.appendTo('#target');

let button: Button = new Button({
    content: 'Show Tooltip'
});
button.appendTo('#target');

```

{% endtab %}

### Scroll mode

When `height` is specified with a certain pixel value and the Tooltip content overflows, the scrolling mode gets enabled.

{% tab template="tooltip/dimensions/scroll-mode", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="scroll-mode-template" %}

```typescript

import { Tooltip } from '@syncfusion/ej2-popups';

let tooltipContent: HTMLElement = document.createElement("div");
tooltipContent.id = 'tooltipContent';
tooltipContent.innerHTML = "<b>Environmentally friendly</b> or environment-friendly, (also referred to as eco-friendly, nature-friendly, and green) are marketing and sustainability terms referring to goods and services, laws, guidelines and policies that inflict reduced, minimal, or no harm upon ecosystems or the environment.";

let tooltip: Tooltip = new Tooltip({
    width: '300px',
    height: '60px',
    content: tooltipContent,
    isSticky: true
});
tooltip.appendTo('#target');

```

{% endtab %}

> The scrolling mode can best be seen when the sticky mode of the Tooltip is enabled. To enable sticky mode, set the `isSticky` property to true.
