---
title: "Add html attributes"
component: "Uploader"
description: "This section describes how to add additional html attributes."
---

# Add html attributes

You can add the additional HTML attributes such as disabled, value, name, and more to the element using the [htmlAttributes](../../api/uploader/#htmlAttributes) property. If you configured both the property and equivalent HTML attribute, then the component considers the property value.

The following example demonstrates how to set attributes in htmlAttributes property in the Uploader.

{% tab template="uploader/html-attr", es5Template="html-template", sourceFiles="app.ts,index.html,index.css" %}

```typescript

import { Uploader } from '@syncfusion/ej2-inputs';

//Initialize the control by preload files
let uploadObj: Uploader = new Uploader({
    autoUpload: false,
    asyncSettings: {
        saveUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Save',
        removeUrl: 'https://ej2.syncfusion.com/services/api/uploadbox/Remove'
    },
    htmlAttributes: {"disabled": "true"}
});
uploadObj.appendTo('#fileupload');

```

{% endtab %}

> You can also explore [JavaScript File Upload](https://www.syncfusion.com/javascript-ui-controls/js-file-upload) feature tour page for its groundbreaking features. You can also explore our [JavaScript File Upload example](https://ej2.syncfusion.com/demos/#/material/uploader/default.html) to understand how to browse the files which you want to upload to the server.