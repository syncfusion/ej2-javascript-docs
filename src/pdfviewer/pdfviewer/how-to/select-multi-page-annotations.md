---
title: "Select multi-page TextMarkup annotation as single annotation"
component: "PDF Viewer"
description: "Learn how to select multi-page TextMarkup Annotation as single annotation for PDF Viewer control."
---

# Select multi-page TextMarkup annotation as single annotation

The PDF Viewer library allows you to select the multi page TextMarkup annotation as a single annotation by enabling the **enableMultiPageAnnotation** property. By default it is false.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to select the multi page TextMarkup annotation as a single annotation, export and import multi page annotation.

```typescript

// Enable multi-page TextMarkup Annotation.
viewer.enableMultiPageAnnotation = true;

// Export Annotation
document.getElementById('export').addEventListener('click', () => {
  viewer.exportAnnotation();
});

// Import Annotation.
document.getElementById('import').addEventListener('click', () => {
  viewer.importAnnotation("Add Export annotation file content");

```

Find the Sample [how to select multi-page TextMarkup annotation as single annotation](https://stackblitz.com/edit/xuyjgt?file=index.ts)