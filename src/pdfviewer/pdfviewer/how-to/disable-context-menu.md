---
title: "Disable Context Menu action"
component: "PDF Viewer"
description: "Learn how to disable Context Menu action programmatically for PDF Viewer control."
---

# Disable Context Menu action

The PDF Viewer library allows you to disable context menu action using the **contextMenuAction** property as `'None'`. Default value of the **contextMenuAction** is `'RightClick'`.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to disable context menu action for PDF viewer control.

```html
<button id='disable'>Disable ContextMenu</button>
```

```typescript

// Disable contextMenu action
document.getElementById('disable').addEventListener('click', ()=> {
viewer.contextMenuOption = 'None';
});

```

Find the Sample [how to disable Context Menu action](https://stackblitz.com/edit/e99te3?devtoolsheight=33&file=index.ts)