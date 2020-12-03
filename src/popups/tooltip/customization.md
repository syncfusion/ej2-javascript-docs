---
title: "Tooltip Customization"
component: "Tooltip"
description: "TypeScript tooltip component’s complete look and feel can be customized by changing its background color, opacity, content font, etc."
---

# Customization

The Tooltip can be customized by using the `cssClass` property, which accepts custom CSS class names that define specific user-defined
 styles and themes to be applied on the Tooltip element.

## Tip pointer customization

Styling the tip pointer's size, background, and border colors can be done using the `cssClass` property, as given below.

{% tab template="tooltip/custom-tip", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css",es5Template="custom-tip-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
let tooltip: Tooltip = new Tooltip({
    cssClass: 'customtip'
});
tooltip.appendTo('#target');

```

{% endtab %}

## Tooltip customization

The complete look and feel of the Tooltip can be customized by changing it's background color, opacity, content font, etc.
 The following code example shows the way to achieve it.

{% tab template="tooltip/custom-tooltip", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="custom-tooltip-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
let tooltip: Tooltip = new Tooltip({
    cssClass: 'customtooltip'
});
tooltip.appendTo('#target');

```

{% endtab %}
