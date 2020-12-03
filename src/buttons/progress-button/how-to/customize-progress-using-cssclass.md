---
title: "Customize progress using cssClass"
component: "ProgressButton"
description: "TypeScript ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Customize progress using cssClass

You can customize the background filler UI using the [`cssClass`](../../api/progress-button#cssClass) property.

* Adding `e-vertical` to `cssClass` shows vertical progress.
* Adding `e-progress-top` to `cssClass` shows progress at the top.

You can also show reverse progress by adding custom class to the [`cssClass`](../../api/progress-button#cssClass) property.

{% tab template="progress-button/custom-progress", sourceFiles="app.ts,index.html,styles.css", es5Template="custom-progress" %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let vertcialProgress: ProgressButton = new ProgressButton({ content: 'Vertical Progress', enableProgress: true, cssClass: 'e-hide-spinner e-vertical', duration: 4000 });

vertcialProgress.appendTo('#vertical');

let topProgress: ProgressButton = new ProgressButton({ content: 'Progress Top', enableProgress: true, cssClass: 'e-hide-spinner e-progress-top', duration: 4000 });

topProgress.appendTo('#top');

let reverseProgress: ProgressButton = new ProgressButton({ content: 'Reverse Progress', enableProgress: true, cssClass: 'e-hide-spinner e-reverse-progress', duration: 4000 });

reverseProgress.appendTo('#reverse');
```

{% endtab %}
