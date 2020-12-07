---
title: "Customization"
component: "ProgressBar"
description: "The progressBar can  be customized in various ways "
---

# Customization

## Segments

<!-- markdownlint-disable MD033 -->

We can divide a progress bar into multiple segments using a `segmentCount` to visualize the progress of multiple sequential tasks.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

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
    errorProgress.appendTo('#percentage');

```

{% endtab %}

## Thickness

 You can customize the thickness of the track  using `trackThickness` and progress using `progressThickness` to render the ProgressBar with different appearances.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

    let percentageProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        width: '90%',
        trackThickness: 24,
        progressThickness: 24,
        value: 100,
        showProgressValue: true,
        labelStyle: {
            color: '#FFFFFF'
        },
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        }
    });
    percentageProgress.appendTo('#percentage');

```

{% endtab %}

## Radius

<!-- markdownlint-disable MD033 -->

The  radius of the progress bar can be customized using `radius` property and  corner can be customized by **cornerRadius** property.  

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

let percentageProgress: ProgressBar = new ProgressBar({
  type: "Circular",
  value: 60,
  width: "160px",
  height: "160px",
  enableRtl: false,
  trackColor: "#FFD939",
  radius: "100%",
  progressColor: "white",
  trackThickness: 80,
  cornerRadius: "Round",
  progressThickness: 10,
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  }
});
percentageProgress.appendTo("#percentage");

```

{% endtab %}

## InnerRadius

<!-- markdownlint-disable MD033 -->

The inner radius of the progress bar can be customized using `innerRadius` property.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

let percentageProgress: ProgressBar = new ProgressBar({
       type: 'Circular',
        value: 60,
        width: '160px',
        height: '160px',
        enableRtl: false,
        trackColor :'#FFD939',
        radius: '100%',
        innerRadius: '80%',
        progressColor: 'white',
        trackThickness: 80,
        cornerRadius: 'Round',
        progressThickness: 10,
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
    percentageProgress.appendTo('#percentage');

```

{% endtab %}

## Progress color and track color

<!-- markdownlint-disable MD033 -->

We can customize the color of progress and track by using  **progressColor** and **trackColor** property.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

        let percentageProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        height: '60',
        width: '90%',
        trackThickness: 24,
        progressThickness: 24,
        cornerRadius: 'Round',
        progressColor: '#E3165B',
        trackColor: '#F8C7D8',
        value: 50,
        showProgressValue: true,
        labelStyle: {
            color: '#FFFFFF'
        },
        animation: {
            enable: true,
            duration: 2000,
            delay: 0,
        },
        textRender: (args: ITextRenderEventArgs) => {
            args.text = '50';
        }
    });
    percentageProgress.appendTo('#percentage');
```

{% endtab %}