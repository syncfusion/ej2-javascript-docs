---
title: "Print the PDF document programmatically"
component: "PDF Viewer"
description: "Learn how to print the PDF document programmatically in PDF Viewer control."
---

# Print the PDF document programmatically

The PDF Viewer library allows you to print the PDF document programmatically using the **print()** method in the **PrintModule**.

The following steps are used to print the PDF document programmatically.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** Add the following code snippet to perform the print operation.

```html
 <button id="print">Print</button>
```

```typescript
document.getElementById('print').addEventListener('click', ()=> {
   //Print the loaded document.
   viewer.printModule.print();
});
```

Find the Sample, [how to print the PDF document programmatically](https://stackblitz.com/edit/j9tu5j-cc3akh?devtoolsheight=33&file=index.ts)