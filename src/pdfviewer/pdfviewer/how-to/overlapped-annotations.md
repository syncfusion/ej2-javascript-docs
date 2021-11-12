---
title: "Get the overlapped annotations on mouse click"
component: "PDF Viewer"
description: "Learn how to get the overlapped annotations on mouse click programmatically for PDF Viewer control."
---

# Get the overlapped annotations on mouse click

The PDF Viewer library allows you to get the overlapped annotations on mouse click. Overlapped annotations on the selected annotation can be defined using the **annotationCollection** property of **annotationSelect** event.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** The following code snippet explains how to get the overlapped annotations on mouse click.

```javascript

// Get overlapped annotation collections.
viewer.annotationSelect =(args) =>{
console.log(args.annotationCollection);
}

```

Find the Sample [how to get the overlapped annotations on mouse click](https://stackblitz.com/edit/a93cem?devtoolsheight=33&file=index.js)