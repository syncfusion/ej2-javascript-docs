---
title: "Hide spinner"
component: "ProgressButton"
description: "TypeScript ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Hide spinner

You can hide spinner in the ProgressButton by setting the `e-hide-spinner` property to [`cssClass`](../../api/progress-button#cssClass).

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html", es5Template="hide-spinner" %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({ content: 'Progress', enableProgress: true, cssClass: 'e-hide-spinner' });

progressBtn.appendTo('#progressbtn');
```

{% endtab %}