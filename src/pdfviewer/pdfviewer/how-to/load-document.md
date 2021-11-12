---
title: "Load PDF documents dynamically"
component: "PDF Viewer"
description: "Learn how to load PDF documents dynamically in PDF Viewer control."
---

# Load PDF documents dynamically

The PDF Viewer library allows to switch or load the PDF documents dynamically after the initial load operation. To achieve this, load the PDF document as a base64 string or file name in PDF Viewer control using the [**Load()**](https://ej2.syncfusion.com/documentation/api/pdfviewer/#load) method dynamically.

The following steps are used to load the PDF document dynamically.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** Use the following code snippet to load PDF document using base64 string.

```html
<button id='load1'>LoadDocumentFromBase64</button>
```

```typescript
// Load PDF document from Base64 string
document.getElementById('load1').addEventListener('click', () => {
  viewer.load(
    'data:application/pdf;base64,'+ AddBase64String, null);
}
```

**Step 3:** Use the following code snippet to load PDF document using document name.

```html
<button id='load2'>LoadDocument</button>
```

```typescript
// Load PDF document using file name
document.getElementById('load2').addEventListener('click', () => {
  viewer.load('PDF_Succinctly.pdf', null);
});

```

Find the sample, [how to load PDF documents dynamically](https://stackblitz.com/edit/1tkfra-a8yca8?devtoolsheight=33&file=index.ts)