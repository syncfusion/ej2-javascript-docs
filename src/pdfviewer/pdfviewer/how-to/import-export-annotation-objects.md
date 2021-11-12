---
title: "Import and Export annotation as object"
component: "PDF Viewer"
description: "Learn how to import and export annotation as object in PDF Viewer control."
---

# Import and Export annotation as object

The PDF Viewer library allows you to import annotations from objects or streams instead of loading it as a file. To import such annotation objects, the PDF Viewer control must export the PDF annotations as objects using the [**ExportAnnotationsAsObject()**](https://ej2.syncfusion.com/javascript/documentation/api/pdfviewer/#exportannotationsasobject) method. Only the annotations objects that are exported from the PDF Viewer can be imported.

The following steps are used to import and export annotation as object.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** Use the following code snippet to perform import and export annotation.

```html
<button id="export">Export Annotation</button>
<button id="import">Import Annotation</button>
```

```js
//Export annotation as object.
document.getElementById('export').addEventListener('click', () => {
  viewer.exportAnnotationsAsObject().then(function(value) {
    exportObject = value;
  });
});

//Import annotation that are exported as object.
document.getElementById('import').addEventListener('click', () => {
  viewer.importAnnotation(JSON.parse(exportObject));
});
```

Find the Sample, [how to import and export annotation as object](https://stackblitz.com/edit/bktnkt?devtoolsheight=33&file=index.js)