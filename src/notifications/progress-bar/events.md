---
title: "Events"
component: "Progress Bar"
description: "Learn here all about events of Syncfusion Progress Bar component and more."
---

# Events

This section describes the Progress Bar events that will be triggered when appropriate actions are performed. Following events are available in the Progress Bar.

* [`valueChanged`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#valuechanged) - When the progress value changes, this event is triggered.

* [`progressCompleted`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#progresscompleted) - When the progress reaches the maximum value, this event is triggered.

* [`animationComplete`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#animationcomplete) - When animation is enabled and the progress to the value is reached, this event is triggered.

* `annotationRender` - Before each annotation is rendered, this event is triggered.

* [`textRender`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#textrender) - Before the progress text is rendered, this event is triggered

* [`load`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#load) - When the control begins to render, this event is triggered.

* [`loaded`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#loaded) - After the control has been rendered, this event is triggered.

* `resized` - When the window is resized, this event is triggered.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import {ProgressBar, ProgressAnnotation, IProgressValueEventArgs ITextRenderEventArgs, IAnnotationRenderEventArgs, ILoadedEventArgs,IProgressResizeEventArgs } from '@syncfusion/ej2-progressbar';
ProgressBar.Inject(ProgressAnnotation);

let progress: ProgressBar = new ProgressBar({
  type: 'Linear',
  trackThickness: 24,
  progressThickness: 24,
  value: 50,
  labelStyle: {
    color: '#FFFFFF'
  },
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  },
  valueChanged: (args: IProgressValueEventArgs) => {
    // Here you can customize the code.
  },
  progressCompleted: (args: IProgressValueEventArgs) => {
    // Here you can customize the code.
  },
  animationComplete: (args: IProgressValueEventArgs) => {
    // Here you can customize the code.
  },
  textRender: (args: ITextRenderEventArgs) => {
    // Here you can customize the code.
  },
  annotationRender: (args: IAnnotationRenderEventArgs) => {
    // Here you can customize the code.
  },
  load: (args: ILoadedEventArgs) => {
    // Here you can customize the code.
  },
  loaded: (args: ILoadedEventArgs) => {
    // Here you can customize the code.
  },
  resized: (args: IProgressResizeEventArgs) => {
    // Here you can customize the code.
  }
});

progress.appendTo('#element');

```

{% endtab %}