---
title: "Rich text editor File Browser"
component: "Rich Text Editor"
description: "This section explains about how to enable the file browser feature in the Syncfusion JavaScript Rich Text Editor control."
---

# File Browser

Rich Text Editor allows to browse and insert an image in the edit panel using the file browser. File browser allows the users to browse and select a file or folder from the file system and it supports various cloud services.

## Required additional package styles and scripts reference

Following packages style and script (local or CDN) reference additionally required to use the file browser feature in Rich Text Editor.

* ej2-data
* ej2-layouts
* ej2-grids
* ej2-filemanager

Map the above packages style and script reference in sample as like below

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
        <title>Essential JS 2 Rich Text Editor</title>

        <!-- Essential JS 2 Rich Text Editor's dependent material themes -->
        <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css" />
        <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css" />
        <!-- Essential JS 2 Rich Text Editor material theme -->
        <link href="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css" />

        <!-- Essential JS 2 Rich Text Editor's dependent scripts -->
        <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 Rich Text Editor's global script -->
        <script src="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js" type="text/javascript"></script>
      </head>
      <body>
      </body>
  </html>
```

The following example explains about how to configure the file browser within the Rich Text Editor component.

* Configure the `FileManager` toolbar item in the `toolbarSettings` API `items` property.
* Set [`enable`](../api/rich-text-editor/fileManagerSettings/#enable) property as `true` on [`fileManagerSettings`](../api/rich-text-editor/#fileManagerSettings) property to make the file browser in the Rich Text Editor to appear on the `FileManager` toolbar click action.

{% tab template="rich-text-editor/file-browser", es5Template="file-browser" %}

```typescript
import { RichTextEditor, HtmlEditor, Toolbar, QuickToolbar, Image, FileManager } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(HtmlEditor, Toolbar, QuickToolbar, Image, FileManager);

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';

let defaultRTE: RichTextEditor = new RichTextEditor({
    fileManagerSettings: {
        enable: true,
        path: '/Pictures/Food',
        ajaxSettings: {
            url: hostUrl + 'api/FileManager/FileOperations',
            getImageUrl: hostUrl + 'api/FileManager/GetImage',
            uploadUrl: hostUrl + 'api/FileManager/Upload',
            downloadUrl: hostUrl + 'api/FileManager/Download'
        }
    },
    toolbarSettings: {
        items: ['FileManager']
    }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}