---
title: "Rich Text Editor file attachments"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to attach the files."
---

# File Attachments

The Rich Text Editor allows you to attach a file based on the file upload. You can attach your files using the file upload or drag-and-drop from your local path. When the file upload gets success, the attachment link inserts into the content.

In the below sample, configure the saveUrl and path properties to achieve file attachments.

        1. saveUrl: Provides service URL to save the files.
        2. path: Specifies the location to store the image.

The following sample illustrates how to attach a file in the Rich Text Editor.

``` HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Rich Text Editor</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Typescript UI Controls" />
    <meta name="author" content="Syncfusion" />
    <link href="index.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-base/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-richtexteditor/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-inputs/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-lists/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-navigations/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-popups/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-buttons/styles/material.css" rel="stylesheet" />
    <link href="{{:CDN_LINK}}ej2-splitbuttons/styles/material.css" rel="stylesheet" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.19.38/system.js"></script>
    <script src="systemjs.config.js"></script>
</head>

<body>
    <div id='loader'>Loading....</div>
    <div id='container'>
        <div id='defaultRTE'>
            <p>The sample is configured with inline mode of editor. Initially, the editor is rendered without a <a href="https://ej2.syncfusion.com/home/" target="_blank">toolbar</a>. The toolbar becomes visible only when the content is selected/clicked.</p>
        </div>
        <div id="fileUpload">
        </div>
    </div>
</body>

</html>
```

``` typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar, NodeSelection } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar, NodeSelection);
import { Uploader } from '@syncfusion/ej2-inputs';

let selection: NodeSelection = new NodeSelection();
let range: Range;
let saveSelection: NodeSelection;
let defaultRTE: RichTextEditor = new RichTextEditor({
  insertImageSettings: {
   saveUrl: "[SERVICE_HOSTED_PATH]/api/uploadbox/Save",
    path: "../Files/"
  }
});
defaultRTE.appendTo("#defaultRTE");
let uploadObj: Uploader = new Uploader({
  asyncSettings: {
    saveUrl: "[SERVICE_HOSTED_PATH]/api/uploadbox/Save",
  },
  dropArea: defaultRTE.inputElement,
  success: onUploadSuccess
});
uploadObj.appendTo("#fileupload");
function onUploadSuccess(args: any): void {
  (defaultRTE.contentModule.getEditPanel() as HTMLElement).focus();
  range = selection.getRange(document);
  saveSelection = selection.save(range, document);
  let fileUrl: any =
      document.URL + defaultRTE.insertImageSettings.path + args.file.name;
  if (defaultRTE.formatter.getUndoRedoStack().length === 0) {
      defaultRTE.formatter.saveData();
  }
  saveSelection.restore();
  defaultRTE.executeCommand('createLink', { url: fileUrl, text: fileUrl, selection: saveSelection });
  defaultRTE.formatter.saveData();
  defaultRTE.formatter.enableUndo(defaultRTE);
  this.clearAll();
}

```

To configure server-side handler, refer the below code.

``` csharp
int x = 0;
string file;
 [AcceptVerbs("Post")]
        public void Save()
        {
            try
            {
                var httpPostedFile = System.Web.HttpContext.Current.Request.Files["UploadFiles"];
                file = httpPostedFile.FileName;
                if (httpPostedFile != null)
                {
                    Console.WriteLine(System.Web.HttpContext.Current.Server.MapPath("~/Files"));
                    var fileSave = System.Web.HttpContext.Current.Server.MapPath("~/Files");
                    if (!Directory.Exists(fileSave))
                    {
                        Directory.CreateDirectory(fileSave);
                    }
                    var fileName = Path.GetFileName(httpPostedFile.FileName);
                    var fileSavePath = Path.Combine(fileSave, fileName);
                    while (System.IO.File.Exists(fileSavePath))
                    {
                        file = "rte" + x + "-" + fileName;
                        fileSavePath = Path.Combine(fileSave, file);
                        x++;
                    }
                    if (!System.IO.File.Exists(fileSavePath))
                    {
                        httpPostedFile.SaveAs(fileSavePath);
                        HttpResponse Response = System.Web.HttpContext.Current.Response;
                        Response.Clear();
                        Response.Headers.Add("name", file);
                        Response.ContentType = "application/json; charset=utf-8";
                        Response.StatusDescription = "File uploaded succesfully";
                        Response.Headers.Add("url", fileSavePath);
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