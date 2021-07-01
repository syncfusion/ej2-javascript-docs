---
title: "Themes"
component: "Progress Bar"
description: "Learn here all about themes of Syncfusion Progress Bar component and more."
---

# Theme

To enhance the visualization of the Progress Bar, use different themes that are mapped to the [`theme`](https://ej2.syncfusion.com/javascript/documentation/api/progressbar/#theme) property. The following themes are available in the Progress Bar.

* Material
* Fabric
* Bootstrap
* Bootstrap 4
* High Contrast
* Tailwind

{% tab template="progressbar/theme", es5Template="es5_progressbar", sourceFiles="index.ts,index.html"  %}

```typescript

import { ProgressBar } from '@syncfusion/ej2-progressbar';

let linearThemeProgress: ProgressBar = new ProgressBar({
  type: 'Linear',
  height: '60',
  width: '100%',
  value: 40,
  secondaryProgress: 60,
  trackThickness: 20,
  progressThickness: 20,
  theme: 'HighContrast',
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  }
});

linearThemeProgress.appendTo('#linearTheme');

let circularThemeProgress: ProgressBar = new ProgressBar({
  type: 'Circular',
  height: '150',
  width: '100%',
  value: 40,
  secondaryProgress: 60,
  trackThickness: 20,
  progressThickness: 20,
  theme: 'HighContrast',
  animation: {
    enable: true,
    duration: 2000,
    delay: 0
  }
});

circularThemeProgress.appendTo('#circularTheme');

```

{% endtab %}