---
title: "Javascript(ES-5) Dialog Getting Started"
component: "Dialog"
description: "Helps to get started with the dialog control along with its key features such as modal dialog, positioning, and draggable."
---

# Getting Started with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript controls.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-popups/dist/global/ej2-popups.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-popups/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" />

            <!-- Essential JS 2 Dialog's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Dialog` element and initiate the `Essential JS 2 Dialog` control in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" />

            <!-- Essential JS 2 Dialog's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>

            <style>
                #container {
                    min-height: 300px;
                }
            </style>
       </head>
       <body>
            <div id="container">
                <!-- Add the HTML <div> element  -->
                <div id="dialog"></div>
            </div>
            <script>
                //Initialize Dialog control
                var dialog = new ej.popups.Dialog({
                    // Dialog content
                    content: 'This is a Dialog with content',
                    // The Dialog shows within the target element
                    target: document.getElementById("container"),
                    // Dialog width
                    width: '250px'
                });
                // Render initialized Dialog
                dialog.appendTo('#dialog');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Dialog** control.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript controls.

**Step 2:** The Essential JS 2 control's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js`](http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Dialog` element and initiate the `Essential JS 2 Dialog` control in the index.html by using following code.

{% tab template="dialog/getting-started",sourceFiles="app.ts,index.html,styles.css",isDefaultActive=true, es5Template="basic-template" %}

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Dialog` control.

> In the dialog control, max-height is calculated based on the dialog target element height. If the target property is not configured, the document.body is considered as a target. Therefore, to show a dialog in proper height, you need to add min-height to the target element.

## Modal dialog

A [modal](../api/dialog/#ismodal) shows an overlay behind the Dialog. So, the user
should interact the Dialog compulsory before interacting with the remaining content in an
application.

While the user clicks the overlay, the action can be handled through the
[`overlayClick`](../api/dialog/#overlayclick) event. In the below sample, the
Dialog close action is performed while clicking on the overlay.

> When the modal dialog is opened, the Dialog's target scrolling will be disabled. The scrolling
will be enabled again once close the Dialog.

{% tab template="dialog/modal",sourceFiles="app.ts,index.html,styles.css", es5Template="modal-template" %}

{% endtab %}

## Enable header

The Dialog header can be enabled by adding the header content as text or HTML content through the
[`header`](../api/dialog/#header) property.

{% tab template="dialog/header",sourceFiles="app.ts,index.html,styles.css", es5Template="header-template" %}

{% endtab %}

## Configure action buttons

The Dialog provides built-in support to render the action buttons on the footer (for ex: 'OK' or
'Cancel' buttons) by using [buttons](../api/dialog/#buttons) property. Each Dialog button allows the user
to perform any action while clicking on it.

The primary button will be focused automatically on open the Dialog, and add the [click](../api/dialog/buttonPropsModel/#click)
event to handle the actions

> When the Dialog initialize with more than one primary buttons, the first primary button gets focus on open the Dialog.

The below sample render with buttons and its action.

{% tab template="dialog/footer",sourceFiles="app.ts,index.html,styles.css", es5Template="footer-template" %}

{% endtab %}

## Draggable

The Dialog supports to [drag](../api/dialog/#allowdragging) within its target
container by grabbing the Dialog header, which allows the user to reposition the
Dialog dynamically.

> The Dialog can be draggable only when the Dialog header is enabled.
From `16.2.x` version, enabled draggable support for modal dialog also.

{% tab template="dialog/draggable",sourceFiles="app.ts,index.html,styles.css", es5Template="draggable-template" %}

{% endtab %}

## Positioning

The Dialog can be positioned using the [position](../api/dialog/#position) property by providing the X and Y co-ordinates. It can be positioned inside the target of the container or `<body>` of the element based on the given X and Y values.

for X is: left, center, right (or) any offset value
for Y is: top, center, bottom (or) any offset value

The below example demonstrates the different Dialog positions.

{% tab template="dialog/positioning",sourceFiles="app.ts,index.html,styles.css", es5Template="position-template" %}

{% endtab %}

## See Also

* [Load dialog content using AJAX](./how-to/load-dialog-content-using-ajax)
* [How to position the dialog on center of the page on scrolling](./how-to/position-the-dialog-on-center-of-the-page-on-scrolling)
* [Prevent closing of modal dialog](./how-to/prevent-closing-of-modal-dialog)
* [Close dialog while click on outside of dialog](./how-to/close-dialog-while-click-on-outside-of-dialog)
* [How to make a reusable alert and confirm dialog](./dialog-utility/)
