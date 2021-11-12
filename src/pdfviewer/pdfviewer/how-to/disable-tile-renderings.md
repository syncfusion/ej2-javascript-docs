---
title: "Disable the tile rendering"
component: "PDF Viewer"
description: "Learn how to disable the tile rendering for PDF Viewer control."
---

# Disable the tile rendering

The PDF Viewer library allows you to disable the tile rendering mode by setting the **enableTileRendering** property as `false`. Default value of the property is `true`. Tile rendering will split the PDF document page into multiple regions and will render each region by region.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to Disable the tile rendering.

```javascript

// Disable tile rendering.
document.getElementById('disable').addEventListener('click', () => {
  viewer.tileRenderingSettings.enableTileRendering = false;
});

```

Find the Sample [how to disable the tile rendering](https://stackblitz.com/edit/7fefpj?file=index.js)