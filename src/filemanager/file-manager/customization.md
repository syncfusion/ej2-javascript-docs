---
title: "Customization"
component: "File Manager"
description: "Customizing File Manager functionalities"
---

# Customizing File Manager functionalities

The file manager component allows customizing its functionalities like, context menu, searching, uploading, toolbar using APIs. Given below are some of the functionalities that can be customized in the File Manager,

* [Context menu customization](#context-menu-customization)
* [Details view customization](#details-view-customization)
* [Navigation pane customization](#navigation-pane-customization)
* [Show/Hide file extension](#showhide-file-extension)
* [Show/Hide hidden items](#showhide-hidden-items)
* [Show/Hide thumbnail images in large icons view](#showhide-thumbnail-images-in-large-icons-view)
* [Toolbar customization](#toolbar-customization)
* [Upload customization](#upload-customization)
* [Tooltip customization](#tooltip-customization)

## Context menu customization

The context menu settings like, items to be displayed on files, folders and layout click and visibility can be customized using [contextMenuSettings](../api/file-manager/#contextmenusettings) property.

{% tab template="file-manager/contextmenu", es5Template="context-menu", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Context Menu settings customization
    contextMenuSettings: { file: ['Open', '|', 'Details'], folder: ['Open', '|', 'Details'], layout: ['SortBy', 'View', 'Refresh', '|', 'Details', '|'], visible: true}
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Details view customization

The details view settings like, column width, header text, template for each field can be customized using [detailsViewSettings](../api/file-manager/#detailsviewsettings) property.

{% tab template="file-manager/detailsview", es5Template="details-view", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Initial view of File Manager is set to details view
    view: "Details",
    // Details View settings customization
    detailsViewSettings: {
        columns: [
            {field: 'name', headerText: 'File Name', minWidth: 120, width: 'auto', customAttributes: { class: 'e-fe-grid-name' },template: '${name}'},
            {field: 'size', headerText: 'File Size',minWidth: 50, width: '110', template: '${size}'},
            { field: '_fm_modified', headerText: 'Date Modified',minWidth: 50, width: '190'}
        ]
    }
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Navigation pane customization

The navigation pane settings like, minimum and maximum width and visibility can be customized using [navigationPaneSettings](../api/file-manager/#navigationpanesettings) property.

{% tab template="file-manager/navigationpane", es5Template="navigation-pane", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Navigation Pane settings customization
    navigationPaneSettings: { maxWidth: '850px', minWidth: '140px', visible: true}
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Show/Hide file extension

The file extensions are displayed in the File Manager by default. This can be hidden by disabling the [showFileExtension](../api/file-manager/#showfileextension) property.

In File Manager [fileLoad](../api/file-manager/#fileload) and [fileOpen](../api/file-manager/#fileopen) events are triggered before the file/folder is rendered and before the file/folder is opened respectively. These events can be utilized to perform operations before a file/folder is rendered or opened.

{% tab template="file-manager/fileextension", es5Template="file-extension", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Hides the file extension in File Manager
    showFileExtension: false,
    // File Manager's fileLoad event
    fileLoad: onBeforeFileLoad,
    // File Manager's fileOpen event
    fileOpen: onBeforeFileOpen
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');

// File Manager's file fileLoad function
function onBeforeFileLoad(args: any){
    console.log(args.fileDetails.name + " is loading");
}

// File Manager's file fileOpen function
function onBeforeFileOpen(args: any){
    console.log(args.fileDetails.name + " is opened");
}
```

{% endtab %}

## Show/Hide hidden items

The File Manager provides support to show/hide the hidden items by enabling/disabling the [showHiddenItems](../api/file-manager/#showhiddenitems) property.

{% tab template="file-manager/hiddenitems", es5Template="hidden-items", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // The default value set for showHiddenItems is false
    showHiddenItems: true
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Show/Hide thumbnail images in large icons view

The thumbnail images are displayed in the File Manager's large icons view by default. This can be hidden by disabling the [showThumbnail](../api/file-manager/#showthumbnail) property.

{% tab template="file-manager/disablethumbnail", es5Template="disable-thumbnail", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Hides the thumbnail images in File Manager's large icons view
    showThumbnail: false
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Toolbar customization

The toolbar settings like, items to be displayed in toolbar and visibility can be customized using [toolbarSettings](../api/file-manager/#toolbarsettings) property.

{% tab template="file-manager/toolbar", es5Template="tool-bar", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Toolbar settings customization
    toolbarSettings: { items: ['NewFolder', 'Refresh', 'View', 'Details'], visible: true}
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Upload customization

The upload settings like, minimum and maximum file size and enabling auto upload can be customized using [uploadSettings](../api/file-manager/#uploadsettings) property.

{% tab template="file-manager/upload", es5Template="upload", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Upload settings customization
    uploadSettings: { maxFileSize: 233332, minFileSize: 120, autoUpload: true}
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}

## Tooltip customization

The tooltip value can be customized by adding extra content to the title of the toolbar, navigation pane, details view and large icons of the file manager element.

{% tab template="file-manager/tooltip", es5Template="tooltip", sourceFiles="app.ts,index.html" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView, FileLoadEventArgs } from '@syncfusion/ej2-filemanager';
import { getValue, select } from '@syncfusion/ej2-base';
import { Tooltip, TooltipEventArgs } from '@syncfusion/ej2-popups';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize file manager component
let fileObj: FileManager = new FileManager({
  ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download',
        getImageUrl: hostUrl + 'api/FileManager/GetImage'
    },
    created: () => { addTooltip(); },
    fileLoad: (args: FileLoadEventArgs) => {
        //Native tooltip customization to display additonal information in new line
        let target: Element = args.element;
        if (args.module==='DetailsView') {
            let element: Element = select('[title]', args.element);
            let title: string = getValue('name', args.fileDetails) +
                '\n' + getValue('dateModified', args.fileDetails);
            element.setAttribute('title', title);
        } else if (args.module==='LargeIconsView') {
            let title: string = getValue('name', args.fileDetails) +
                '\n' + getValue('dateModified', args.fileDetails);
            target.setAttribute('title', title);
        }
    }
});

// render initialized FileManager
fileObj.appendTo('#filemanager');

function addTooltip() {
    let tooltip: Tooltip = new Tooltip({
        target: '#' + fileObj.element.id + '_toolbar [title]',
        beforeRender: onTooltipBeforeRender
    });
    tooltip.appendTo('#' + fileObj.element.id + '_toolbar');
}

function onTooltipBeforeRender(args: TooltipEventArgs) {
    let buttonId: string = select('button', args.target).id;
    let description: string = '';
    switch (buttonId) {
        case fileObj.element.id + '_tb_newfolder':
            description = 'Create a new folder';
            break;
        case fileObj.element.id + '_tb_upload':
            description = 'Upload new files';
            break;
        case fileObj.element.id + '_tb_cut':
            description = 'Cut files and folders from the current location';
            break;
        case fileObj.element.id + '_tb_copy':
            description = 'Copy files and folders from the current location';
            break;
        case fileObj.element.id + '_tb_paste':
            description = 'Paste files and folders in the current location';
            break;
        case fileObj.element.id + '_tb_delete':
            description = 'Delete selected files and folders';
            break;
        case fileObj.element.id + '_tb_download':
            description = 'Download selected files and folders';
            break;
        case fileObj.element.id + '_tb_rename':
            description = 'Rename selected file or folder';
            break;
        case fileObj.element.id + '_tb_sortby':
            description = 'Change the file sorting order';
            break;
        case fileObj.element.id + '_tb_refresh':
            description = 'Refresh the current location';
            break;
        case fileObj.element.id + '_tb_selection':
            description = 'Following items are currently selected:';
            for (let i: number = 0; i < fileObj.selectedItems.length; i++) {
                description = description + '</br>' + fileObj.selectedItems[i];
            }
            break;
        case fileObj.element.id + '_tb_view':
            description = 'Switch the layout view';
            break;
        case fileObj.element.id + '_tb_details':
            description = 'Get the details of the seletced items';
            break;
        default:
            description = '';
            break;
    }
    this.content = args.target.getAttribute('title') + '</br>' + description;
}
```

{% endtab %}