---
title: "Right-To-Left"
component: "Button"
description: "TypeScript Button how to section, block button, repeat button, tooltip for Button, customization of button appearance, input and anchor elements."
---

# Right-To-Left

Button component has RTL support. This can be achieved by setting [`enableRtl`](../../api/button#enablertl) as
`true`.

The following example illustrates how to enable right-to-left support in Button component.

{% tab template= "button/howto", sourceFiles="app.ts,index.html,styles.css", es5Template="rtl-btn-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let button: Button = new Button({iconCss: 'e-btn-icons e-setting-icon', content: 'Settings', enableRtl: true}, '#custombtn');

```

{% endtab %}