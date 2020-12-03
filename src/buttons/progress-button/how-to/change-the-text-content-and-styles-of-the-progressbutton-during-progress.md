---
title: "Change the text content and styles of the ProgressButton during progress"
component: "ProgressButton"
description: "TypeScript ProgressButton how to section, change text content and styles, hide spinner, customize progress."
---

# Change the text content and styles of the ProgressButton during progress

You can change the text content and styles of the ProgressButton during progress by changing the text content and the [`cssClass`](../../api/progress-button#cssClass) property at the [`begin`](../../api/progress-button#begin) and [`end`](../../api/progress-button#end) events.

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html", es5Template="content-change", isDefaultActive=true %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let uploadBtn: ProgressButton = new ProgressButton({
    content: 'Upload',
    cssClass: 'e-hide-spinner',
    enableProgress: true,
    duration: 4000,
    begin: () => {
        uploadBtn.content = 'Uploading...';
        uploadBtn.cssClass = 'e-hide-spinner e-info';
        uploadBtn.dataBind();
    },
    end: () => {
        uploadBtn.content = 'Success';
        uploadBtn.cssClass = 'e-hide-spinner e-success';
        uploadBtn.dataBind();
        setTimeout(() => {
            uploadBtn.content = 'Upload';
            uploadBtn.cssClass = 'e-hide-spinner';
            uploadBtn.dataBind();
        }, 500)
    }
}, '#progressbtn');

```

{% endtab %}