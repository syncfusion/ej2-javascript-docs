---
title: "Create a Block Button"
component: "Button"
description: "TypeScript Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Create a Block Button

You can customize a Button into a Block Button that will span the entire width of its parent element. To create a Block Button,
set the [`cssClass`](../../api/button#cssclass) property to `e-block`.

{% tab template= "button/block", sourceFiles="app.ts,index.html,styles.css",
es5Template="block-btn-template", isDefaultActive=true %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Block Button.
let button: Button = new Button({cssClass: `e-block`});
button.appendTo('#blockbtn');

//Primary Block Button.
button = new Button({ isPrimary: true, cssClass: `e-block` });
button.appendTo('#primarybtn');

//Success Block Button.
button = new Button({ cssClass: `e-block e-success` });
button.appendTo('#successbtn');
```

{% endtab %}