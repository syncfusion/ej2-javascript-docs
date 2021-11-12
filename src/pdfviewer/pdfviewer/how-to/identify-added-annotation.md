---
title: "Identify added annotation mode"
component: "PDF Viewer"
description: "Learn how to identify added annotation mode programmatically for PDF Viewer control."
---

# Identify added Annotation mode

The PDF Viewer library allows you to identify whether the added annotations in PDF document is UI drawn, imported or existing annotation. Annotation mode can be identified using the **annotationAddMode** property of **annotationSelect** event.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** The following code snippet explains how to identify added annotation mode.

```javascript

viewer.annotationSelect =(args) =>{
console.log(args.annotationAddMode);
}

```

Find the Sample [how to identify added annotation mode](https://stackblitz.com/edit/xntzu8?devtoolsheight=33&file=index.js)
