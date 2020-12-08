# How to add custom thumbnail in file manager

The default appearance of the file manager can customize with your own icon by using [showThumbnail](../../api/file-manager/#showthumbnail) property.

The following example demonstrate how to add a custom icon in largeicons view.

{% tab template="file-manager/custom-thumbnail", es5Template="custom-thumbnail", sourceFiles="app.ts,index.html,index.css" %}

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
    showThumbnail: false,
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}