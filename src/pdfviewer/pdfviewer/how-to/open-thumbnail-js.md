---
title: "Open Thumbnail pane programmatically"
component: "PDF Viewer"
description: "Learn how to open the thumbnail pane programmatically in PDF Viewer control."
---

# Open Thumbnail pane programmatically

The PDF Viewer library allows you to open the thumbnail pane programmatically using the [**openThumbnailPane()**](https://ej2.syncfusion.com/javascript/documentation/api/pdfviewer/thumbnailView/#openthumbnailpane) method.

The following steps are used to open the thumbnail.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create a simple PDF Viewer sample.

**Step 2:** Use the following code snippet to open thumbnail.

```html
<button id="openThumbnail">Open Thumbnail Pane</button>
```

```js
document.getElementById('openThumbnail').addEventListener('click', () => {
  // Open Thumbnail pane
  viewer.thumbnailViewModule.openThumbnailPane();
});
```

Find the sample, [how to open the thumbnail pane programmatically](https://stackblitz.com/edit/ejvemx?file=index.js)