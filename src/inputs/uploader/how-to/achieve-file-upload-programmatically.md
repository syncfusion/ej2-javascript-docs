---
title: "Achieve file upload programmatically"
component: "Uploader"
description: "Covers customizable features of the file upload control such as a preview image, invisible upload, progress bar, sort the file list and more."
---

# Achieve file upload programmatically

You can upload a file programmatically using the [upload](../../api/uploader/#upload) method.
Get the selected files data from the [getFilesData](../../api/uploader/#getfilesdata) public method in uploader.

The upload method behaves differently based on its arguments.
* If this method receives any files as arguments, those files only start to upload.
* If it has no argument, all the selected files start to upload.

{% tab template="uploader/dynamic-upload", es5Template="upload-dynamic", sourceFiles="app.ts,index.html,index.css" %}

```typescript
import { Uploader } from '@syncfusion/ej2-inputs';

//Initialize the control by preload files
let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    }
});
uploadObj.appendTo('#fileupload');

document.getElementById('first').onclick = (args) => {
    uploadObj.upload(uploadObj.getFilesData()[0]);
};

document.getElementById('full').onclick = (args) => {
    uploadObj.upload(uploadObj.getFilesData());
};
```

{% endtab %}

> You can also explore [JavaScript File Upload](https://www.syncfusion.com/javascript-ui-controls/js-file-upload) feature tour page for its groundbreaking features. You can also explore our [JavaScript File Upload example](https://ej2.syncfusion.com/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.