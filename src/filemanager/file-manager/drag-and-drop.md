---
title: "Drag and Drop"
component: "File Manager"
description: "Drag and Drop Support in file manager"
---

# Drag And Drop

The file manager allows files or folders to be moved from one folder to another by using the  [allowDragAndDrop](../api/file-manager/#allowdraganddrop) property. It also supports uploading a file by dragging it from Windows Explorer to  FileManager control. You can enable or disable this support by using the [allowDragAndDrop](../api/file-manager/#allowdraganddrop) property of file manager.

The event triggered in drag and drop support are

* [fileDragStart](../api/file-manager/#filedragstart) - Triggers when the file/folder dragging is started.
* [fileDragging](../api/file-manager/#filedragging) - Triggers while dragging the file/folder.
* [fileDragStop](../api/file-manager/#filedragstop) - Triggers when the file/folder is about to be dropped at the target.
* [fileDropped](../api/file-manager/#filedropped) - Triggers when the file/folder is dropped.

{% tab template="file-manager/drag-and-drop", es5Template="drag-and-drop", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize file manager component and add custom item to contextmenu
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    allowDragAndDrop: true, // allowDragAndDrop is false by default.
     // File Manager's file drag start event
    fileDragStart: onFileDragStart,
     // File Manager's file dragging event
    fileDragging: onFileDragging,
    // File Manager's file drag stop event
    fileDragStop: onFileDragStop,
    // File Manager's file drag stop event
    fileDropped: onFileDropped

});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');

// File Manager's file drag start event function
function onFileDragStart(args: any){
    console.log("File drag start");
}
// File Manager's file drag stop event function
function onFileDragStop(args: any){
    console.log("File drag stop");
}
// File Manager's file dragging event function
function onFileDragging(args: any){
    console.log("File dragging");
}
// File Manager's file dropped event function
function onFileDropped(args: any){
    console.log("File dropped");
}

```

{% endtab %}