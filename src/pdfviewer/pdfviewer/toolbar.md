---
title: "Toolbar"
component: "PDF Viewer"
description: "Learn about the built-in Toolbar in PDF Viewer."
---

# Built-in toolbar

The PDF Viewer comes with a powerful built-in toolbar to execute important actions such as page navigation, text search,view mode,download,print,bookmark, and thumbnails.

The following table shows built-in toolbar items and its actions:-

| Option | Description |
|---|---|
| OpenOption | This option provides an action to load the PDF documents to the PDF Viewer.|
| PageNavigationTool | This option provides an action to navigate the pages in the PDF Viewer. It contains GoToFirstPage,GoToLastPage,GotoPage,GoToNext, and GoToLast tools.|
| MagnificationTool | This option provides an action to magnify the pages either with predefined or user defined zoom factors in the PDF Viewer. Contains ZoomIn, ZoomOut, Zoom, FitPage and FitWidth tools|
| PanTool |This option provides an action for panning the pages in the PDF Viewer.|
| SelectionTool |This option provides an action to enable/disable the text selection in the PDF Viewer.|
| SearchOption |This option provides an action to search a word in the PDF documents.|
| PrintOption |This option provides an action to print the PDF document being loaded in the PDF Viewer.|
| DownloadOption |This Download option provides an action to download the PDF document that has been loaded in the PDF Viewer.|
| UndoRedoTool | This tool provides options to undo and redo the annotation actions performed in the PDF Viewer.|
| AnnotationEditTool | This tool provides options to enable or disable the edit mode of annotation in the PDF Viewer.|
| FormDesignerEditTool | This tool provides options to enable or disable the edit mode of form fields in the PDF Viewer.|

## Show/Hide the default toolbar

The PDF Viewer has an option to show or hide the complete default toolbar. You can achieve this by using following two ways.,

```html

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Essential JS 2</title>
<!-- Essential JS 2 fabric theme -->
<link href="{{:CDN_LINK}}ej2-pdfviewer/styles/fabric.css" rel="stylesheet" type="text/css"/>
<!-- Essential JS 2 PDF Viewer's global script -->
<script src="{{:CDN_LINK}}dist/ej2.min.js" type="text/javascript"></script>
</head>
<body>
<!--element which is going to render-->
<div id='container'>
<div id='PdfViewer' style="height:500px;width:100%;">
</div>
</div>
</body>
</html>

```

* **Show/Hide toolbar using enableToolbar API as in the following code snippet**

{% tab template="pdfviewer/es5-toolbar/toolbar-hide",  sourceFiles="index.html" %}

```javascript

var pdfviewer = new ej.pdfviewer.PdfViewer({
                    enableToolbar: false,
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer'
                });
ej.pdfviewer.PdfViewer.Inject(ej.pdfviewer.TextSelection, ej.pdfviewer.TextSearch, ej.pdfviewer.Navigation,ej.pdfviewer.Print);
pdfviewer.appendTo('#PdfViewer');

```

{% endtab %}

* **Show/Hide toolbar using showToolbar as in the following code snippet**

{% tab template="pdfviewer/es5-toolbar/toolbar-method",  sourceFiles="index.html" %}

```javascript

var pdfviewer = new ej.pdfviewer.PdfViewer({
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer'
                });
ej.pdfviewer.PdfViewer.Inject(ej.pdfviewer.TextSelection, ej.pdfviewer.TextSearch, ej.pdfviewer.Navigation,ej.pdfviewer.Print);
pdfviewer.appendTo('#PdfViewer');
pdfviewer.toolbar.showToolbar(false);

```

{% endtab %}

## Show/Hide the default toolbaritem

The PDF Viewer has an option to show or hide these grouped items in the default toolbar.

* **Show/Hide toolbaritem using toolbarSettings as in the following code snippet.**

{% tab template="pdfviewer/es5-toolbar/toolbar-items", sourceFiles="index.html" %}

```javascript

var pdfviewer = new ej.pdfviewer.PdfViewer({
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer',
                    toolbarSettings: { showTooltip : true, toolbarItem: ['OpenOption']}
                });
ej.pdfviewer.PdfViewer.Inject(ej.pdfviewer.TextSelection, ej.pdfviewer.TextSearch, ej.pdfviewer.Navigation,ej.pdfviewer.Print);
pdfviewer.appendTo('#PdfViewer');

```

{% endtab %}

* **Show/Hide toolbaritem using showToolbaritem as in the following code snippet**

{% tab template="pdfviewer/es5-toolbar/toolbar-items-method", sourceFiles="index.html" %}

```javascript

var pdfviewer = new ej.pdfviewer.PdfViewer({
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer',
                });
ej.pdfviewer.PdfViewer.Inject(ej.pdfviewer.TextSelection, ej.pdfviewer.TextSearch, ej.pdfviewer.Navigation,ej.pdfviewer.Print);
pdfviewer.appendTo('#PdfViewer');
pdfviewer.toolbar.showToolbarItem(["OpenOption"],false);

```

{% endtab %}

## See also

* [Toolbar customization](./how-to/customization)
* [Feature Modules](./feature-module)