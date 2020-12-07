---
title: "Types"
component: "ProgressBar"
description: "The ProgressBar Visualize the progress in different shapes"
---

# Types

Visualize progress in different shapes (rectangle, circle, and semi-circle) to give a unique appearance to your app design.

## Linear

Set **type** to Linear to get the linear progress bar. It also support secondary progress and different mode of progress.

{% tab template="progressbar/types", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let uploadProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        value: 100,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        }
    });
    uploadProgress.appendTo('#lineardeterminate');
    let successProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        isIndeterminate: true,
        value: 20,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    successProgress.appendTo('#linearindeterminate');
    let warningsProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        value: 40,
        secondaryProgress: 60,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    warningsProgress.appendTo('#linearbuffer');
    let errorProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        segmentCount: 8,
        value: 100,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    errorProgress.appendTo('#linearsegment');

```

{% endtab %}

## Circular

Set **type** to Circular to get the circular progress bar. It also support secondary progress and different mode of progress.

{% tab template="progressbar/types", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript


import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let uploadProgress: ProgressBar = new ProgressBar({
        type: 'Circular',
        height: '60',
        value: 100,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        }
    });
    uploadProgress.appendTo('#lineardeterminate');
    let successProgress: ProgressBar = new ProgressBar({
        type: 'Circular',
        height: '60',
        isIndeterminate: true,
        value: 20,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    successProgress.appendTo('#linearindeterminate');
    let warningsProgress: ProgressBar = new ProgressBar({
        type: 'Circular',
        height: '60',
        value: 40,
        secondaryProgress: 60,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    warningsProgress.appendTo('#linearbuffer');
    let errorProgress: ProgressBar = new ProgressBar({
        type: 'Circular',
        height: '60',
        segmentCount: 8,
        value: 100,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    });
    errorProgress.appendTo('#linearsegment');

```

{% endtab %}