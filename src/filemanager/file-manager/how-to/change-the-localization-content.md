# Change the file manager localization content

The example below shows how to modify the file manager component localization content. The upload text of the file manager component can be changed in the following example.

{% tab template="file-manager/locale",sourceFiles="app.ts,index.html", es5Template="locale-text" %}

```typescript
import { FileManager, Toolbar, NavigationPane, DetailsView } from '@syncfusion/ej2-filemanager';
import { L10n } from '@syncfusion/ej2-base';

FileManager.Inject(Toolbar, NavigationPane, DetailsView)


L10n.load({
    'en': {
        'filemanager': {
            // Change the File Upload text.
           "File-Upload": "Files to Upload",
           // Change the Empty folder text.
           "Folder-Empty": "Empty Folder",
        }
    }
})

let hostUrl: string = 'https://ej2-aspcore-service.azurewebsites.net/';
// initialize File Manager component.
let filemanagerInstance: FileManager = new FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    //defining the locale for File Manager
    locale: 'en'
});

// render initialized FileManager
filemanagerInstance.appendTo('#filemanager');
```

{% endtab %}
