---
title: "Highlight, Underline and Strikeout text programmatically"
component: "PDF Viewer"
description: "Learn how to highlight, underline and strikeout text programmatically for PDF Viewer control."
---

# Highlight, Underline and Strikeout text programmatically

The PDF Viewer library allows you to highlight, underline and strikeout text in the loaded PDF document programmatically using the **setAnnotationMode()** method.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to highlight, underline, and strikeout text in the loaded document with button click events.

```javascript

    document.getElementById('setHighlight').addEventListener('click', ()=> {
    viewer.annotation.setAnnotationMode('Highlight');
    });
    document.getElementById('setUnderline').addEventListener('click', ()=> {
    viewer.annotation.setAnnotationMode('Underline');
    });
    document.getElementById('setStrikeout').addEventListener('click', ()=> {
    viewer.annotation.setAnnotationMode('Strikethrough');
    });
    document.getElementById('setNone').addEventListener('click', ()=> {
    viewer.annotation.setAnnotationMode('None');
    });

```

Find the Sample [how to highlight, underline and strikeout text programmatically](https://stackblitz.com/edit/bf3k6y?devtoolsheight=33&file=index.js)