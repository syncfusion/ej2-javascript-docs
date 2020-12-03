---
title: " Rich text editor restricts the image uploading while uploading with large size"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains about, how to restrict the image to upload, when the given image size is greater than the allowed size"
---

# Restrict the image uploading while uploading with large size

By using the Rich text editor's `imageUploading` event, you can get the image size before uploading and restrict the image to upload, when the given image size is greater than the allowed size.

In the following, we have validated the image size before uploading and determined whether the image has been uploaded or not.

{% tab template="rich-text-editor/how-to-check-file-size", es5Template="file-size", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { RichTextEditor, Toolbar, Image,  Link, HtmlEditor, QuickToolbar, NodeSelection } from '@syncfusion/ej2-richtexteditor';
import { UploadingEventArgs } from '@syncfusion/ej2-inputs';
RichTextEditor.Inject(Toolbar, Image,  Link, HtmlEditor, QuickToolbar );

let defaultRTE: RichTextEditor = new RichTextEditor({
        height: 400,
        toolbarSettings: {
        items: ['Undo', 'Redo', '|',
                'Bold', 'Italic', 'Underline', 'StrikeThrough', '|',
                'FontName', 'FontSize', 'FontColor', 'BackgroundColor', '|',
                'SubScript', 'SuperScript', '|',
                'LowerCase', 'UpperCase', '|',
                'Formats', 'Alignments', '|', 'OrderedList', 'UnorderedList', '|',
                'Indent', 'Outdent', '|', 'Image', '|', 'SourceCode',
                '|', 'ClearFormat', 'Print']
        },
         insertImageSettings: {
            saveUrl: "https://aspnetmvc.syncfusion.com/services/api/uploadbox/Save",
            path: "../Images/"
        },
        imageUploading: onImageUploading
    });
    defaultRTE.appendTo("#defaultRTE");

    function onImageUploading(args: UploadingEventArgs): void {
    console.log("file is uploading");
    let imgSize = 500000;
    let sizeInBytes: number = args.fileData.size;
    if ( imgSize < sizeInBytes ) {
        args.cancel = true;
    }
    }

```

{% endtab %}