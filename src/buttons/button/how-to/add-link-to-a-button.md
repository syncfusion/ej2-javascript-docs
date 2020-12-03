---
title: "Add link to a Button"
component: "Button"
description: "TypeScript Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Add link to a Button

The appearance of the Button can be changed like a link by `e-link` class using [`cssClass`](../../api/button#cssclass)
property and link navigation can be handled in Button click.

In the following example, link is added in Button click by using `window.open()` method.

{% tab template= "button/link", sourceFiles="app.ts,index.html,styles.css", es5Template="link-template" %}

```typescript

import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple} from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize the Button component.
let button: Button = new Button({cssClass: 'e-link'});

// Render initialized button.
button.appendTo('#element');

button.element.onclick = (): void => {
    window.open("https://www.google.com");
}

```

{% endtab %}