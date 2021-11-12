---
title: "Add Header values"
component: "PDF Viewer"
description: "Learn how to Add Header values programmatically for PDF Viewer control."
---

# Add Header values

The PDF Viewer library allows you to add header values for every Ajax request send from the PDF viewer. Header values can be added using the **ajaxHeaders** property available in the **ajaxRequestSettings** module.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** The following code snippet explains how to add header values.

```javascript

viewer.ajaxRequestSettings ={
    ajaxHeaders: [
        {
        headerName: "Authorization",

        headerValue: "Bearer 64565dfgfdsjweiuvbiuyhiueygf"
        }
    ],

    withCredentials: false
};

```

Find the Sample [how to add Header values](https://stackblitz.com/edit/o4ywqi?file=index.js)