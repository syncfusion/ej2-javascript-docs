---
title: "Getting Started"
component: "File Manager"
description: "Explains to get started with File Manager control with its default functionality."
---
# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

Create an app folder `myapp` in local machine to initialize Essential JS 2 JavaScript components.

Using either of the following way to refer the required script and styles.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2/confirm) build installed location.

**Step 2:** To render file manager component, need to add file manager and its dependent packages from below installed location.

#### Dependencies

* ej2-base
* ej2-layouts
* ej2-popups
* ej2-data
* ej2-inputs
* ej2-lists
* ej2-buttons
* ej2-splitbuttons
* ej2-navigations
* ej2-grids
* ej2-filemanager

**Syntax:**

> package: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}`

**Example:**

> Package: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\17.1.0.36\Web (Essential JS 2)\JavaScript\ej2-base`
>
> packages: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\17.1.0.36\Web (Essential JS 2)\JavaScript\ej2-inputs`
>
> Package: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\17.1.0.36\Web (Essential JS 2)\JavaScript\ej2-filemanager`
>

**Step 3:** Create a folder `myapp/resources` and copy/paste the above mentioned packages from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 File Manager Component</title>
            <!-- File Manager and its dependent theme -->
            <link href=" resources/ej2-base/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-inputs/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-popups/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-buttons/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-splitbuttons/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-layouts/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-navigations/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-grids/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-filemanager/styles/material.css" rel="stylesheet" />
            <!-- Essential JS 2 File-Manager's global script -->
            <script src="resources/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="resources/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="resources/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="resources/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

>Note: If you want to refer the combined component styles, please make use of our [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

**Step 5:** Now, add the `div` element and initiate the `Essential JS 2 File Manager` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 File Manager Component</title>
            <!-- File Manager and its dependent theme -->
            <link href=" resources/ej2-base/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-inputs/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-popups/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-buttons/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-splitbuttons/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-layouts/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-navigations/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-grids/styles/material.css" rel="stylesheet" />
            <link href=" resources/ej2-filemanager/styles/material.css" rel="stylesheet" />
            <!-- Essential JS 2 File-Manager's global script -->
            <script src="resources/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="resources/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="resources/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="resources/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // initialize File Manager component
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations'
                  }
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

>**Note:** The [ajaxSettings](../api/file-manager/#ajaxsettings) must be defined while initializing the file manager. File manager utilizes the URL's mentioned in ajaxSettings to send [file operation](./file-operations) request to the server.
>The File Manager service link is given in `hostUrl`.

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 file manager** component.

### Using CDN link for script and style reference

**Step 1:** The Essential JS 2 components scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Style: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js`](https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css`](https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css)
>

**Step 2:** Have to add `CDN` global script and style for file manager and its dependent packages in `myapp/index.html` like below.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // initialize File Manager component
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations'
                  }
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

>When referencing CDN links in application, always ensure the network connection will be in enabled state.

The following example shows the basic file manager.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // initialize File Manager component
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations'
                  }
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

{% endtab %}

## File Download support

To perform the download operation, initialize the `downloadUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager component.

```html
<script>
        var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
        // initialize File Manager component
        var filemanagerInstance = new ej.filemanager.FileManager({
            ajaxSettings: {
                url: hostUrl + 'api/FileManager/FileOperations',
                downloadUrl: hostUrl + 'api/FileManager/Download'
            }
        });
        // render initialized File Manager
        filemanagerInstance.appendTo('#filemanager');
</script>
```

## File Upload support

To perform the upload operation, initialize the `uploadUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager Component.

```html
<script>
        var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
        // initialize File Manager component
        var filemanagerInstance = new ej.filemanager.FileManager({
            ajaxSettings: {
                url: hostUrl + 'api/FileManager/FileOperations',
                uploadUrl: hostUrl + 'api/FileManager/Upload'
            }
        });
        // render initialized File Manager
        filemanagerInstance.appendTo('#filemanager');
</script>
```

## Image Preview support

To perform the image preview support in the File Manager component, need to initialize the `getImageUrl` property in a [ajaxSettings](../api/file-manager/#ajaxsettings) of File Manager component.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="https://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // initialize File Manager component
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations',
                      getImageUrl: hostUrl + 'api/FileManager/GetImage'
                  }
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

{% endtab %}

## Injecting feature modules

Basically, the file manager component contains a context menu for performing file operations, large-icons view for displaying the files and folders, and a breadcrumb for navigation. However, these basic functionalities can be extended by using the additional feature modules like toolbar, navigation pane, and details view to simplify the navigation and file operations within the file system. The above modules can be injected using the `ej.filemanager.FileManager.Inject()` method in the script as follows.

```javascript
var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
// inject feature modules of the file manager
ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
// initialize File Manager component
var filemanagerInstance = new ej.filemanager.FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    }
});
// render initialized File Manager
filemanagerInstance.appendTo('#filemanager');
```

The following example shows you the File Manager with all feature modules.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="https://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // inject feature modules of the file manager
              ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
              // initialize File Manager componentej.filemanager.NavigationPane);
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations',
                      getImageUrl: hostUrl + 'api/FileManager/GetImage',
                      uploadUrl: hostUrl + 'api/FileManager/Upload',
                      downloadUrl: hostUrl + 'api/FileManager/Download'
                  }
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

{% endtab %}

>**Note:** The appearance of the File Manager can be customized by using [cssClass](../api/file-manager/#cssclass) property. This adds a css class to the root of the File Manager which can be used to add new styles or override existing styles to the File Manager.

## Switching initial view of the File Manager

The initial view of the File Manager can be changed to details or largeicons view with the help of [view](../api/file-manager/#view) property. By default, the File Manager will be rendered in large icons view. When the File Manager is initially rendered, [created](../api/file-manager/#created) will be triggered. This event can be utilized for performing operations once the File Manager has been successfully created.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // inject feature modules of the file manager
              ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
              // initialize File Manager componentej.filemanager.NavigationPane);
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations',
                      getImageUrl: hostUrl + 'api/FileManager/GetImage',
                      uploadUrl: hostUrl + 'api/FileManager/Upload',
                      downloadUrl: hostUrl + 'api/FileManager/Download'
                  },
                  // Initial view of File Manager is set to details view
                  view: "Details",
                  // File Manager's created event
                  created: onCreate
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
              // File Manager's created event function
              function onCreate(args){
                   console.log("File Manager has been created successfully");
              }
            </script>
       </body>
  </html>
```

{% endtab %}

## Maintaining component state on page reload

The File Manager supports maintaining the component state on page reload. This can be achieved by enabling [enablePersistence](../api/file-manager/#enablepersistence) property which maintains the following,
* Previous view of the File Manager - [View](../api/file-manager/#view)
* Previous path of the File Manager - [Path](../api/file-manager/#path)
* Previous selected items of the File Manager - [SelectedItems](../api/file-manager/#selecteditems)

For every operation in File Manager, ajax request will be sent to the server which then processes the request and sends back the response. When the ajax request is success, [success](../api/file-manager/#success) event will be triggered and [failure](../api/file-manager/#failure) event will be triggered if the request gets failed.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // inject feature modules of the file manager
              ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
              // initialize File Manager componentej.filemanager.NavigationPane);
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations',
                      getImageUrl: hostUrl + 'api/FileManager/GetImage',
                      uploadUrl: hostUrl + 'api/FileManager/Upload',
                      downloadUrl: hostUrl + 'api/FileManager/Download'
                  },
                  enablePersistence: true,
                  // File Manager's onSuccess event
                  success: onAjaxSuccess,
                  // File Manager's onError event
                  failure: onAjaxFailure
             });

            // render initialized File Manager
            filemanagerInstance.appendTo('#filemanager');

            // File Manager's file onSuccess function
            function onAjaxSuccess(args){
                  console.log("Ajax request successful");
            }

            // File Manager's file onError function
            function onAjaxFailure(args){
                  console.log("Ajax request has failed");
            }
            </script>
       </body>
  </html>
```

{% endtab %}

>**Note:** The files of the current folder opened in the File manager can be refreshed programatically by calling [refreshFiles](../api/file-manager/#refreshfiles) method.

## Rendering component in right-to-left direction

It is possible to render the File Manager in right-to-left direction by setting the [enableRtl](../api/file-manager/#enablertl) API to true.

{% tab template="file-manager/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
      <head>
            <title>Essential JS 2 file manager Component</title>
            <!-- file manager and its dependent theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-filemanager/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 file manager's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-filemanager/dist/global/ej2-filemanager.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="filemanager"></div>
            <script>
              var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
              // inject feature modules of the file manager
              ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
              // initialize File Manager componentej.filemanager.NavigationPane);
              var filemanagerInstance = new ej.filemanager.FileManager({
                  ajaxSettings: {
                      url: hostUrl + 'api/FileManager/FileOperations',
                      getImageUrl: hostUrl + 'api/FileManager/GetImage',
                      uploadUrl: hostUrl + 'api/FileManager/Upload',
                      downloadUrl: hostUrl + 'api/FileManager/Download'
                  },
                  enableRtl: true
              });
              // render initialized File Manager
              filemanagerInstance.appendTo('#filemanager');
            </script>
       </body>
  </html>
```

{% endtab %}

## Specifying the current path of the File Manager

The current path of the File Manager can be specified initially or dynamically using the [path](../api/file-manager/#path) property.

```javascript
var hostUrl = 'https://ej2-aspcore-service.azurewebsites.net/';
// inject feature modules of the file manager
ej.filemanager.FileManager.Inject(ej.filemanager.DetailsView,ej.filemanager.Toolbar,ej.filemanager.NavigationPane);
// initialize File Manager componentej.filemanager.NavigationPane);
var filemanagerInstance = new ej.filemanager.FileManager({
    ajaxSettings: {
        url: hostUrl + 'api/FileManager/FileOperations',
        getImageUrl: hostUrl + 'api/FileManager/GetImage',
        uploadUrl: hostUrl + 'api/FileManager/Upload',
        downloadUrl: hostUrl + 'api/FileManager/Download'
    },
    // Specify the required current path
    path: '/Food'
});
// render initialized File Manager
filemanagerInstance.appendTo('#filemanager');
```