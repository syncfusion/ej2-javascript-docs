---
title: "Annotation and Label"
component: "ProgressBar"
description: "The Essential JS 2 ProgressBar component  supports the annotation and label"
---

# Annotation and Label

## Annotation

In the circular progress bar, you can add any view to the center using the **Content** property in annotation.

For example, you can include add, start, or pause button to control the progress. You can also add an image that indicates the actual task in progress or add custom text that conveys how far the task is completed.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript
import { ProgressBar, ProgressAnnotation } from "@syncfusion/ej2-progressbar";
ProgressBar.Inject(ProgressAnnotation);

let percentageProgress: ProgressBar = new ProgressBar({
  type: "Circular",
  innerRadius: "190%",
  trackThickness: 80,
  cornerRadius: "Round",
  trackColor: "#FFD939",
  annotations: [
    {
      content:
        '<div id="point1" style="font-size:20px;font-weight:bold;color:#ffffff;fill:#ffffff"><span>60%</span></div>'
    }
  ]
});
percentageProgress.appendTo("#percentage");

```

{% endtab %}

## Label

You can show the progress value in both linear and circular progress bar using **showProgressValue** property.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript
import { ProgressBar, ITextRenderEventArgs } from "@syncfusion/ej2-progressbar";

let percentageProgress: ProgressBar = new ProgressBar({
        type: 'Linear',
        trackThickness: 24,
        progressThickness: 24,
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