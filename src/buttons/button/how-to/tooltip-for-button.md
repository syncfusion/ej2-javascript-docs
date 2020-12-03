---
title: "Tooltip for Button"
component: "Button"
description: "TypeScript Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Tooltip for Button

Tooltip can be shown on Button hover and it can be achieved by setting `title` attribute.

The following snippets illustrates how to show tooltip on Button hover.

{% tab template= "button/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="tooltip-template" %}

```typescript

import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize the Button component.
let button: Button = new Button({isPrimary: true, content: 'Button'});

// Render initialized button.
button.appendTo('#element');

button.element.setAttribute("title", "Primary Button");

```

{% endtab %}