---
title: "Images"
component: "DocumentEditor"
description: "Learn the supported image types in JavaScript document editor and how to insert, resize, format images."
---

# Images

Document Editor supports common raster format images like PNG, BMP, JPEG, and GIF. You can insert an image file or online image in the document using the `insertImage()` method. Refer to the following sample code.

{% tab template="document-editor/image",es5Template="image" , sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Editor, Selection, ImageResizer, EditorHistory } from '@syncfusion/ej2-documenteditor';
import { Button } from '@syncfusion/ej2-buttons';
//Inject require modules.
DocumentEditor.Inject(Editor, Selection, ImageResizer, EditorHistory);
let documenteditor: DocumentEditor = new DocumentEditor({
      isReadOnly: false,
      enableEditor: true,
      enableSection: true,
      enableImageResizer: true,
      enableEditorHistory: true,
      height: '370px'
});
documenteditor.appendTo('#DocumentEditor');

let insertPictureButton: Button = new Button();
insertPictureButton.appendTo('#insert-picture');

//Open file picker.
document.getElementById('insert-picture').addEventListener('click', () => {
      let pictureUpload: HTMLInputElement = document.getElementById("insertImageButton") as HTMLInputElement;
      pictureUpload.value = '';
      pictureUpload.click();
});
// File picker change event.
document.getElementById('insertImageButton').addEventListener('change', onInsertImage);

//Get select image from file picker and insert it in Document Editor.
function onInsertImage(args: any): void {
    if (navigator.userAgent.match('Chrome') || navigator.userAgent.match('Firefox') || navigator.userAgent.match('Edge') || navigator.userAgent.match('MSIE') || navigator.userAgent.match('.NET')) {
        if (args.target.files[0]) {
            let path = args.target.files[0];
            let reader = new FileReader();
            reader.onload = function (frEvent: any) {
                let base64String = frEvent.target.result;
                let image = document.createElement('img');
                image.addEventListener('load', function () {
                    //Insert image.
                    documenteditor.editor.insertImage(base64String, this.width, this.height);
                })
                image.src = base64String;
            };
            reader.readAsDataURL(path);
        }
        //Safari does not Support FileReader Class
    } else {
        let image = document.createElement('img');
        image.addEventListener('load', function () {
            documenteditor.editor.insertImage(args.target.value);
        })
        image.src = args.target.value;
    }
}
```

{% endtab %}

Image files will be internally converted to base64 string. Whereas, online images are preserved as URL.

## Image resizing

Document Editor provides built-in image resizer that can be injected into your application based on the requirements. This allows you to resize the image by dragging the resizing points using mouse or touch interactions. This resizer appears as follows.

![Image](images/image.png)

## Changing size

Document Editor expose API to get or set the size of the selected image. Refer to the following sample code.

```typescript
documenteditor.selection.imageFormat.width = 800;
documenteditor.selection.imageFormat.height = 800;
```

>Note: Images are stored and processed(read/write) as base64 string in DocumentEditor. The online image URL is preserved as a URL in DocumentEditor upon saving.

## Text wrapping style

Text wrapping refers to how images fit with surrounding text in a document. Please [refer to this page](../document-editor/text-wrapping-style) for more information about text wrapping styles available in Word documents.

## Positioning the image

DocumentEditor preserves the position properties of the image and displays the image based on position properties. It does not support modifying the position properties. Whereas the image will be automatically moved along with text edited if it is positioned relative to the line or paragraph.

## See Also

* [Feature modules](../document-editor/feature-module/)
