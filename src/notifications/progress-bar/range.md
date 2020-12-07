---
title: "Range"
component: "ProgressBar"
description: "The ProgressBar Visualize the ProgressBar range"
---

# Range

<!-- markdownlint-disable MD033 -->
Range represents the entire span of the ProgressBar and can be defined using the `minimum` and `maximum` properties.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let uploadProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        trackThickness: 24,
        progressThickness: 24,
        value: 90,
        minimum: 10,
        maximum:90,
        showProgressValue: true,
        cornerRadius: 'Round',
        labelStyle: {
            color: '#FFFFFF'
        },
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        }
    });
    uploadProgress.appendTo('#linearsegment');

```

{% endtab %}