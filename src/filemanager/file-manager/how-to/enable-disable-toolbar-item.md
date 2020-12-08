# How to enable/disable toolbar item/items

The toolbar items can be enabled/disabled by specifying the items in [enableToolbarItems](../../api/file-manager/#enabletoolbaritems) or [disableToolbarItems](../../api/file-manager/#disabletoolbaritems) methods respectively.

The following example shows enabling and disabling toolbar items on button click.

{% tab template="file-manager/toolbar-items", es5Template="toolbar-items", sourceFiles="app.ts,index.html,index.css" %}

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
    height: "330px"
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');

// Click event for enable button
document.getElementById("enable").onclick = function(args) {
    // Enable new folder toolbar item
    filemanagerInstance.enableToolbarItems(["newfolder"]);
}

// Click event for enable button
document.getElementById("disable").onclick = function(args) {
    // Disable new folder toolbar item
    filemanagerInstance.disableToolbarItems(["newfolder"]);
}

```

{% endtab %}