---
title: "States"
component: "ProgressBar"
description: "Visualize progress in different states."
---

# States

Visualize progress in different states.

## Determinate

<!-- markdownlint-disable MD033 -->

This is the default state. You can use it when the progress estimation is known.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let percentageProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        value: 100,
    });
    percentageProgress.appendTo('#percentage');
```

{% endtab %}

## Indeterminate

By enabling the **IsIndeterminate** property, the state of the progress bar can be changed to indeterminate when the progress cannot be estimated or is not being calculated. It can be combined with determinate mode to know that the application is estimating progress before the actual progress starts.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';
    let percentageProgress: ProgressBar = new ProgressBar({
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
    percentageProgress.appendTo('#percentage');

```

{% endtab %}

## Buffer

<!-- markdownlint-disable MD033 -->
You can use a secondary progress indicator when the primary progress depends on the secondary progress. This will allow users to visualize both primary and secondary progress simultaneously.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let percentageProgress: ProgressBar = new ProgressBar({
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
    percentageProgress.appendTo('#percentage');

```

{% endtab %}