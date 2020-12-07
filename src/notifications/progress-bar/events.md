---
title: "Events"
component: "ProgressBar"
description: "Visualize progress events"
---

# Events

## Value Change

<!-- markdownlint-disable MD033 -->

valueChanged event is triggered when the progress value is changed.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar, IProgressValueEventArgs } from "@syncfusion/ej2-progressbar";

let percentageProgress: ProgressBar = new ProgressBar({
  type: "Linear",
  trackThickness: 24,
  progressThickness: 24,
  value: 90,
  showProgressValue: true,
  cornerRadius: "Round",
  labelStyle: {
    color: "#FFFFFF"
  },
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  },

  valueChanged: (args: IProgressValueEventArgs) => {
    percentageProgress.progressColor = '#2BB20E';
  }
});
percentageProgress.appendTo("#percentage");
let replayBtn: HTMLElement = document.getElementById("value") as HTMLElement;
replayBtn.onclick = () => {
  percentageProgress.value = 50;
};

```

{% endtab %}

## ProgressCompleted

Triggers when the ProgressBar attains the maximum value.

{% tab template="progressbar/progressbar", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar, IProgressValueEventArgs } from '@syncfusion/ej2-progressbar';
let percentageProgress: ProgressBar = new ProgressBar({
  type: "Linear",
  trackThickness: 24,
  progressThickness: 24,
  value: 100,
  showProgressValue: true,
  cornerRadius: "Round",
  labelStyle: {
    color: "#FFFFFF"
  },
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  },

  progressCompleted: (args: IProgressValueEventArgs) => {
    args.progressColor = '#2BB20E';
  }
});
percentageProgress.appendTo("#percentage");

```

{% endtab %}