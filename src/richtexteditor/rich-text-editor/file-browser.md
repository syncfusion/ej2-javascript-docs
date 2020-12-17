---
title: "Rich text editor File Browser"
component: "Rich Text Editor"
description: "This section explains about how to enable the file browser feature in the Syncfusion JavaScript Rich Text Editor control."
---

# File Browser

Rich Text Editor allows to browse and insert an image in the edit panel using the file browser. File browser allows the users to browse and select a file or folder from the file system and it supports various cloud services.

The following example explains about how to configure the file browser within the Rich Text Editor component.

* Configure the `FileManager` toolbar item in the `toolbarSettings` API `items` property.
* Set [`enable`](../api/rich-text-editor/fileManagerSettings/#enable) property as `true` on [`fileManagerSettings`](../api/rich-text-editor/#fileManagerSettings) property to make the file browser in the Rich Text Editor to appear on the `FileManager` toolbar click action.

> Rich Text Editor features are segregated into individual feature-wise modules. To use file browser tool, inject FileManager module using the `RichTextEditor.Inject(FileManager)`.

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