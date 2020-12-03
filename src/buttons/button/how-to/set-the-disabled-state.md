---
title: "Set the disabled state"
component: "Button"
description: "TypeScript Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Set the disabled state

Button component can be enabled/disabled by giving [`disabled`](../../api/button#disabled) property. To disable Button component,
the `disabled` property can be set as `true`.

The following example demonstrates Button in `disabled` state.

{% tab template= "button/howto", sourceFiles="app.ts,index.html,styles.css", es5Template="disable-btn-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let button: Button = new Button({content: 'Disabled', disabled: true}, '#custombtn');

```

{% endtab %}