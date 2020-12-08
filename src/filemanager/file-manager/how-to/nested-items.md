# Nested FileManager

FileManager can be rendered inside the other components like Tab, Dialog, and more.

* [Adding file manager inside the dialog](#adding-file-manager-inside-the-dialog)
* [Adding  file manager inside the tab](#adding-file-manager-inside-the-tab)

## Adding file manager inside the dialog

The following example shows the file manager component rendered inside the dialog. Click the browse button in the Uploader element to open the File Manager inside the Dialog control.

{% tab template="file-manager/file-upload", es5Template="file-upload", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';
import { Dialog } from '@syncfusion/ej2-popups';
import { FileManager, FileOpenEventArgs, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';
import { Button } from '@syncfusion/ej2-buttons';;

FileManager.Inject(Toolbar, NavigationPane, DetailsView)

// Initialize the Uploader component
let uploadObject: Uploader = new Uploader();
uploadObject.appendTo('#fileupload');

// Initialize the Button component
let btnObj: Button = new Button();
btnObj.appendTo('#openBtn');

// Initialize the Dialog component
let dialogObj: Dialog = new Dialog({
    header: 'Open',
    showCloseIcon: true,
    closeOnEscape: false,
    width: '850px',
    visible: false,
    target: document.getElementById('target'),
    animationSettings: { effect: 'None' },
    open: dialogOpen,
    close: dialogClose
});
dialogObj.appendTo('#dialog');

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
document.getElementById('openBtn').onclick = (): void => {
    dialogObj.show();
    // Initialize the FileManager component
    let filemanagerInstance: FileManager = new FileManager({
        ajaxSettings: {
            url: hostUrl + 'api/FileManager/FileOperations',
            getImageUrl: hostUrl + 'api/FileManager/GetImage',
            uploadUrl: hostUrl + 'api/FileManager/Upload',
            downloadUrl: hostUrl + 'api/FileManager/Download'
        },
        allowMultiSelection: false,
        fileOpen : onFileOpen
    });
    filemanagerInstance.appendTo('#filemanager');
    dialogOpen();
};

// Uploader will be shown, if Dialog is closed
function dialogClose(): void {
    let filemanager: FileManager = (document.getElementById('filemanager') as any).ej2_instances[0];
    filemanager.destroy();
    document.getElementById('container').style.display = 'block';
}

// Uploader will be hidden, if Dialog is opened
function dialogOpen(): void {
    document.getElementById('container').style.display = 'none';
}

// File Manager's fileOpen event function
function onFileOpen(args: FileOpenEventArgs): void {
    let file: any = (args as any).fileDetails;
    if (file.isFile) {
        args.cancel = true;
        uploadObject.files = [{name: file.name, size: file.size, type: file.type }];
        dialogObj.hide();
    }
}

```

{% endtab %}

## Adding file manager inside the tab

The following example demonstrate that the file manager component is placed inside the content area of tab element.

{% tab template="file-manager/file-tab", es5Template="file-tab", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { enableRipple } from '@syncfusion/ej2-base';
import { Tab } from '@syncfusion/ej2-navigations';
import { FileManager, Toolbar, NavigationPane, DetailsView, ContextMenu } from '@syncfusion/ej2-filemanager';
FileManager.Inject(Toolbar, NavigationPane, DetailsView, ContextMenu);
enableRipple(true);


//Initialize Tab component
let tabObj: Tab = new Tab({
    heightAdjustMode: 'None',
    height: 320,
    showCloseButton: true,
    selected: onSelect,
});
//Render initialized Tab component
tabObj.appendTo('#tab_orientation');


let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
let fileObject: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    view: 'Details'
});
fileObject.appendTo('#filemanager');
function onSelect(): void  {
   fileObject.refreshLayout();
}

```

{% endtab %}