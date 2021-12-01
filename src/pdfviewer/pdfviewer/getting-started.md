---
title: "Getting Started with JavaScript(ES5)"
component: "PDF Viewer"
description: "Learn how to get started using JavaScript(global script) PDF Viewer component through simple steps."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2/) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/JavaScript - EJ2/{RELEASE_VERSION}/Web(Essential JS 2)/JavaScript/{PACKAGE_NAME}/dist/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/JavaScript - EJ2/{RELEASE_VERSION}/Web(Essential JS 2)/JavaScript/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/JavaScript - EJ2/19.3.53/Web(Essential JS 2)/JavaScript/ej2/dist/ej2.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/JavaScript - EJ2/19.3.53/Web(Essential JS 2)/JavaScript/ej2-js-es5/styles/material.css`

You can also clone the [`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

**Step 3:** Create a folder `myapp/resources` and copy/paste the scripts and styles of ej2 package from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/ej2-js-es5/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 PDF Viewer's script -->
            <script src="resources/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Div` element and initiate the `Essential JS 2 PDF Viewer` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>
          <!-- Essential JS 2 material theme -->
          <link href="resources/ej2-js-es5/styles/material.css" rel="stylesheet" type="text/css"/>

          <!-- Essential JS 2 PDF Viewer's script -->
          <script src="resources/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
          <!--element which is going to render-->
          <div id="container">
               <div id="PdfViewer" style="display:block;height:580px;width:100%;">
               </div>
          </div>
          <script>
               //Initialize PDF Viewer component
               var pdfviewer = new ej.pdfviewer.PdfViewer({
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer'
               });
               //PDF Viewer control rendering starts
               pdfviewer.appendTo('#PdfViewer');
          </script>
       </body>
  </html>
```

> For PDF Viewer serviceUrl creation, follow the steps provided in the [link](https://ej2.syncfusion.com/documentation/pdfviewer/how-to/create-pdfviewer-service/)

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 PDF Viewer** component as below.

![JavaScript Output](../../pdfviewer/images/javascript_output.png)

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

> Script: [`https://cdn.syncfusion.com/ej2/dist/ej2.min.js`](https://cdn.syncfusion.com/ej2/dist/ej2.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/material.css`](https://cdn.syncfusion.com/ej2/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Div` element and initiate the `Essential JS 2 PDF Viewer` component in the index.html by using following code.

{% tab template="pdfviewer/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
     <head>
          <title>Essential JS 2</title>
          <!-- Essential JS 2 material theme -->
          <link href="https://cdn.syncfusion.com/ej2/material.css" rel="stylesheet">

          <!-- Essential JS 2 PDF Viewer's script -->
          <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
     </head>
     <body>
          <!--element which is going to render-->
          <div id="container">
               <div id="PdfViewer" style="height:580px;width:100%;">
               </div>
          </div>
          <script>
               //Initialize PDF Viewer component
               var pdfviewer = new ej.pdfviewer.PdfViewer({
                    documentPath: "PDF_Succinctly.pdf",
                    serviceUrl: 'https://ej2services.syncfusion.com/production/web-services/api/pdfviewer'
               });
               ej.pdfviewer.PdfViewer.Inject(ej.pdfviewer.TextSelection, ej.pdfviewer.TextSearch, ej.pdfviewer.Navigation,ej.pdfviewer.Print);
               //PDF Viewer control rendering starts
               pdfviewer.appendTo('#PdfViewer');
          </script>
          <script>
               var ele = document.getElementById('container');
               if(ele) {
                    ele.style.visibility = "visible";
               }
        </script>
     </body>
</html>
```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 PDF Viewer` component.
