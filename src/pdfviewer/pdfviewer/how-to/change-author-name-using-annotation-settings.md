---
title: "How to change the author name using AnnotationSettings"
component: "PDF Viewer"
description: "Learn how to change the author name using AnnotationSettings in the Syncfusion.EJ2.PDFViewer library."
---

# Change the author name using AnnotationSettings

The Essential JavaScript PDF Viewer supports to customize a single property of the annotation settings by exposing an API for the properties common to all the annotations.

**API Name** : annotationSettings

|Property Name|Data type & Default Value|Description|
|---|---|---|
|author|String(“Guest”)|specifies the author of the annotation.|
|minWidth|Number(0)|specifies the minWidth of the annotation.|
|maxWidth|Number(0)|specifies the maxWidth of the annotation.|
|minHeight|Number(0)|specifies the minHeight of the annotation.|
|maxHeight|Number(0)|specifies the maxHeight of the annotation.|
|isLock|Boolean(false)|specifies the locked action of the annotations. [If set true unable to select the annotations]|
|isPrint|Boolean(true)|specifies whether the annotations are included or not in Print actions.|
|isDownload|Boolean(true|specifies whether the annotations are included or not in Download actions.|
|Free Text Settings|
|allowOnlyTextInput|Boolean(false)|specifies the allow only text action of the free text annotation. [If set true unable to move or resize the annotations]|

You can change the author name and the other properties using the annotationSettings API as in the following code sample.

```typescript
import { PdfViewer, Toolbar, Magnification, Navigation, LinkAnnotation, ThumbnailView, BookmarkView, TextSelection, TextSearch, Print, Annotation, FormFields } from "../src/index";

PdfViewer.Inject(Toolbar, Magnification, Navigation, LinkAnnotation, ThumbnailView, BookmarkView, TextSelection, TextSearch, Print, Annotation, FormFields);
let viewer: PdfViewer = new PdfViewer();
viewer.serviceUrl = "https://ej2services.syncfusion.com/production/web-services/api/pdfviewer";
viewer.load('PDF_Succinctly.pdf', null);
viewer.annotationSettings = { author: 'syncfusion', minHeight: 30, maxHeight: 500, minWidth: 30, maxWidth: 500, isLock: false, isPrint: true, isDownload: true  };
viewer.freeTextSettings = { allowTextOnly : true };
viewer.appendTo("#pdfViewer");
```