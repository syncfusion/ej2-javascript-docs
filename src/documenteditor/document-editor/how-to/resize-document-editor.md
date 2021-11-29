---
title: "how to resize document editor"
component: "DocumentEditor"
description: "Learn how to change height and width of JavaScript Document Editor component."
---

# How to change height and width of of JavaScript Document Editor component

In this article, we are going to see how to change height and width of Documenteditor.

## Change height of Document Editor

DocumentEditorContainer initially render with default height. You can change height of documenteditor using [`height`](../../api/document-editor-container/documentEditorContainerModel/#height) property, the value which is in pixel.

The following example code illustrates how to change height of Document Editor.

```typescript

let container: DocumentEditorContainer = new DocumentEditorContainer({
    enableToolbar:true, height: "590px"
});
container.appendTo('#DocumentEditor');

```

Similarly, you can use [`height`](../../api/document-editor#height) property for DocumentEditor also.

## Change width of Document Editor

DocumentEditorContainer initially render with default width. You can change width of documenteditor using [`width`](../../api/document-editor-container/documentEditorContainerModel/#width) property, the value which is in percent.

The following example code illustrates how to change width of Document Editor.

```typescript

let container: DocumentEditorContainer = new DocumentEditorContainer({
    enableToolbar:true, width: "100%"
});
container.appendTo('#DocumentEditor');

```

Similarly, you can use [`width`](../../api/document-editor#width) property for DocumentEditor also.

## Resize Document Editor

Using [`resize`](../../api/document-editor-container#resize) method, you change height and width of Document editor.

The following example code illustrates how to fit Document Editor to browser window size.

```typescript
import {
  DocumentEditorContainer,
  Toolbar,
} from '@syncfusion/ej2-documenteditor';

let container: DocumentEditorContainer = new DocumentEditorContainer({enableToolbar: true,height: '590px'});
DocumentEditorContainer.Inject(Toolbar);
container.serviceUrl =
  'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';

container.created = (): void => {
  setInterval(() => {
    updateDocumentEditorSize();
  }, 100);
  //Adds event listener for browser window resize event.
  window.addEventListener('resize', onWindowResize);
};
container.appendTo('#container');

function onWindowResize() {
  //Resizes the document editor component to fit full browser window automatically whenever the browser resized.
  updateDocumentEditorSize();
}
function updateDocumentEditorSize() {
  //Resizes the document editor component to fit full browser window.
  var windowWidth = window.innerWidth;
  var windowHeight = window.innerHeight;
  container.resize(windowWidth, windowHeight);
}
```