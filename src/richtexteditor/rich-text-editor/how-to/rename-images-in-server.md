---
title: "How To rename uploaded images before inserting in Rich Text Editor"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to rename images in server and get the updated name for the image."
---

# Rename uploaded images in server before inserting it in the Rich Text Editor

By using the [`insertImageSettings`](./../../api/rich-text-editor/imageSettings/#imageSettings) property, you can specify the server handler to upload the selected images. Then you can bind the [`imageUploadSuccess`](./../../api/rich-text-editor/imageSuccessEventArgs/#imageSuccessEventArgs) event, to receive the modified file name from the server and update it in the Rich Text Editor's insert image dialog.

```HTML
<div id='defaultRTE'>
    <p>The Rich Text Editor is WYSIWYG ("what you see is what you get") editor useful to create and edit content, and return the valid <a href="https://ej2.syncfusion.com/home/" target="_blank">HTML markup</a> or <a href="https://ej2.syncfusion.com/home/" target="_blank">markdown</a> of the content</p>
    <p><b>Key features:</b></p>
    <ul>
        <li>
            <p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p>
        </li>
        <li>
            <p>Capable of handling markdown editing.</p>
        </li>
        <li>
            <p>Contains a modular library to load the necessary functionality on demand.</p>
        </li>
    </ul>
</div>
```

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
        toolbarSettings: {
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough','|',
                'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
                'LowerCase', 'UpperCase', '|',
                'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
                'Outdent', 'Indent', '|',
                'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
                'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
        },
        insertImageSettings: {
            saveUrl: "[SERVICE_HOSTED_PATH]/api/uploadbox/Rename",
            path: "../Images/"
        },
        imageUploadSuccess: onImageUploadSuccess
    });
defaultRTE.appendTo('#defaultRTE');

function onImageUploadSuccess (args: any) {
    alert("Get the new file name here");
    if (args.e.currentTarget.getResponseHeader('name') != null) {
        args.file.name = args.e.currentTarget.getResponseHeader('name');
        let filename: any = document.querySelectorAll(".e-file-name")[0];
        filename.innerHTML = args.file.name.replace(document.querySelectorAll(".e-file-type")[0].innerHTML, '');
        filename.title = args.file.name;
    }
}

```

To configure server-side handler, refer the below code.

```csharp
int x = 0;
string file;
[AcceptVerbs("Post")]
public void Rename()
{
    try
    {
        var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
        imageFile = httpPostedFile.FileName;
        if (httpPostedFile != null)
        {
            var fileSave = System.Web.HttpContext.Current.Server.MapPath("~/Images");
            if (!Directory.Exists(fileSave))
            {
                Directory.CreateDirectory(fileSave);
            }
            var fileName = Path.GetFileName(httpPostedFile.FileName);
            var fileSavePath = Path.Combine(fileSave, fileName);
            while (System.IO.File.Exists(fileSavePath))
            {
                imageFile = "rteImage" + x + "-" + fileName;
                fileSavePath = Path.Combine(fileSave, imageFile);
                x++;
            }
            if (!System.IO.File.Exists(fileSavePath))
            {
                httpPostedFile.SaveAs(fileSavePath);
                HttpResponse Response = System.Web.HttpContext.Current.Response;
                Response.Clear();
                Response.Headers.Add("name", imageFile);
                Response.ContentType = "application/json; charset=utf-8";
                Response.StatusDescription = "File uploaded succesfully";
                Response.End();
            }
        }
    }
    catch (Exception e)
    {
        HttpResponse Response = System.Web.HttpContext.Current.Response;
        Response.Clear();
        Response.ContentType = "application/json; charset=utf-8";
        Response.StatusCode = 204;
        Response.Status = "204 No Content";
        Response.StatusDescription = e.Message;
        Response.End();
    }
}

```
