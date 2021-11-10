---
title: "How to disable optimized text measuring approach"
component: "DocumentEditor"
description: "Learn how to disable optimized text measuring approach in Document Editor and retain the document pagination behavior like v19.2.0.x and older versions."
---

# How to disable optimized text measuring in JavaScript Document Editor component

Starting from v19.3.0.x, the accuracy of text size measurements in Document editor is improved such as to match Microsoft Word pagination for most Word documents. This improvement is included as default behavior along with an optional API `enableOptimizedTextMeasuring` in Document editor settings.  

If you want the Document editor component to retain the document pagination (display page-by-page) behavior like v19.2.0.x and older versions. Then you can disable this optimized text measuring improvement, by setting `false` to [`enableOptimizedTextMeasuring`](../../api/document-editor/documentEditorSettingsModel/#enableoptimizedtextmeasuring) property of  JavaScript Document Editor component.

## Disable optimized text measuring in `DocumentEditorContainer` instance

The following example code illustrates how to disable optimized text measuring improvement in `DocumentEditorContainer` instance.

```typescript
import { DocumentEditorContainer, Toolbar } from '@syncfusion/ej2-documenteditor';

DocumentEditorContainer.Inject(Toolbar);

let container: DocumentEditorContainer = new DocumentEditorContainer({ enableToolbar: true, height: '590px' });

// Disable optimized text measuring improvement
container.documentEditorSettings = { enableOptimizedTextMeasuring: false };

container.serviceUrl =  'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';

container.appendTo('#container');

```

## Disable optimized text measuring in `DocumentEditor` instance

The following example code illustrates how to disable optimized text measuring improvement in `DocumentEditor` instance.

```typescript

import { DocumentEditor } from '@syncfusion/ej2-documenteditor';

let documenteditor: DocumentEditor = new DocumentEditor({ isReadOnly: false, height: '370px', serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/' });

documenteditor.enableAllModules();

// Disable optimized text measuring improvement
documenteditor.documentEditorSettings = {enableOptimizedTextMeasuring: false};

documenteditor.appendTo('#DocumentEditor');

```