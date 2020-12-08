---
title: "Multiple Selection"
component: "File Manager"
description: "Multiple Selection present in file manager"
---

# Multiple Selection

The file manager allows you to select multiple files by enabling the [allowMultiSelection](../api/file-manager/#allowmultiselection) property (enabled by default). The multiple selection can be done by pressing the `Ctrl` key or `Shift` key and selecting the files. The check box can also be used to do multiple selection. `Ctrl + A` can be used to select all files in the current directory. The [fileSelect](../api/file-manager/#fileselect) event will be triggered when the items of file manager control is selected or unselected.

{% tab template="file-manager/multiselect", es5Template="multiselect-template", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize file manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    allowMultiSelection:true, // allowMultiSelection is true by default.
     // File Manager's file select event
    fileSelect: onFileSelect
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');

// File Manager's file select event function
function onFileSelect(args: any){
    console.log(args.fileDetails.name + " has been " + args.action + "ed");
}

```

{% endtab %}

>Note: The File Manager has support to select files and folders initially or dynamically by specifying their names in [selectedItems](../api/file-manager/#selecteditems) property.