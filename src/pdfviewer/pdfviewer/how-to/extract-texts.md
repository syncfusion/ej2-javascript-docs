---
title: "Extract Text"
component: "PDF Viewer"
description: "Learn how to extract text programmatically for PDF Viewer control."
---

# Extract Text

The PDF Viewer library allows you to extract the text from a page along with the bounds. Text extraction can be done using the **isExtractText** property and **extractTextCompleted** event.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** The following code snippet explains how to extract the text from a page.

```typescript

    viewer.isExtractText = true;
    viewer.extractTextCompleted = args => {
    // Extract the Complete text of load document
    console.log(args);
    console.log(args.documentTextCollection[1]);
    // Extract the Text data.
    console.log(args.documentTextCollection[1][1].TextData);
    // Extract Text in the Page.
    console.log(args.documentTextCollection[1][1].PageText);
    // Extracts the first text of the PDF document along with its bounds
    console.log(args.documentTextCollection[1][1].TextData[0].Bounds);

```

Find the Sample [how to Extract Text](https://stackblitz.com/edit/3xmbg6?devtoolsheight=33&file=index.ts)
