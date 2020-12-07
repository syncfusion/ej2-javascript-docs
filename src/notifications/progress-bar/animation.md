---
title: "Animation"
component: "ProgressBar"
description: "ProgressBar support to animate the track."
---

# Animation

<!-- markdownlint-disable MD033 -->

Progress Bar support to animate the progress by using `animation` property. Enable the animation by setting **enable** property and also you can control the speed by using **duration** property.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

       let percentageProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        trackThickness: 24,
        progressThickness: 24,
        value: 100,
        showProgressValue: true,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0
        }
    });
   percentageProgress.appendTo('#percentage');

```

{% endtab %}