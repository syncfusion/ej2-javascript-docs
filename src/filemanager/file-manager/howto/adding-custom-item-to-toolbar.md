# How to add custom button in toolbar

The toolbar items can be customized using the [toolbarSettings](../../api/file-manager/#toolbarSettings) API and [toolbarClick](../../api/file-manager/#toolbarClick) events.

The following example shows adding a custom item in the toolbar.

The new toolbar button is added using [toolbarSettings](../../api/file-manager/#toolbarSettings). The [toolbarClick](../../api/file-manager/#toolbarClick) event is used to add an event handler to the new toolbar button.

{% tab template="file-manager/toolbar", es5Template="toolbar-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView, ToolbarClickEventArgs } from '@syncfusion/ej2-filemanager';

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
    //Custom item added along with default item
    toolbarSettings:{items: ['NewFolder', 'Custom', 'Upload', 'Delete', 'Download', 'Rename', 'SortBy', 'Refresh', 'Selection', 'View', 'Details']},
    toolbarClick:toolbarClick
});

// event for custom toolbar item
function toolbarClick(args: ToolbarClickEventArgs) {
    if (args.item.text === 'Custom') {
        alert('You have clicked custom toolbar item')
    }
}

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}