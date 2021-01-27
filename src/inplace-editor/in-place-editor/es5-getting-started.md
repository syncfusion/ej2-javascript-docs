---
title: "Getting Started ES-5"
component: "In-place Editor"
description: "Learn how to create an Essential JS 2 In-place Editor control in a JavaScript (ES-5) application with its basic features."
---

# Getting Started with JavaScript (ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in the latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for the script and style reference.

### Using local script and style references in an HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript controls.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-inplace-editor/dist/global/ej2-inplace-editor.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-inplace-editor/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create an HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 - In-place Editor</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 In-place Editor's global script -->
            <script src="resources/ej2-inplace-editor.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `In-place Editor` element and initiate the `Essential JS 2 In-place Editor` control in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <ink href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 In-place Editor's global script -->
            <script src="resources/ej2-inplace-editor.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
                var editObj = new ej.inplaceeditor.InPlaceEditor({
                    type: 'Text',
                    value: 'Andrew',
                    model: {
                        placeholder: 'Enter employee name'
                    }
                });
                //Render initialized In-place Editor control
                editObj.appendTo('#element');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 In-place Editor** control.

### Using CDN link for the script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript controls.

**Step 2:** The Essential JS 2 control's global scripts and styles are already hosted in the following CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-inplace-editor/dist/global/ej2-inplace-editor.min.js`](http://cdn.syncfusion.com/ej2/ej2-inplace-editor/dist/global/ej2-inplace-editor.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-inplace-editor/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-inplace-editor/styles/material.css)

**Step 3:** Create an HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `In-place Editor` element and initiate the `Essential JS 2 In-place Editor` control in the index.html by using the following code.

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 In-place Editor` control.

## Configuring DropDownList

You can render the Essential JS 2 DropDownList by changing the [`type`](../api/inplace-editor/inputType/) property as [`DropDownList`](../api/drop-down-list) and configure its properties and methods using the `model` property.

In the following sample, [`type`](../api/inplace-editor/inputType/) and model values are configured to render the [`DropDownList`](../api/drop-down-list) control.

`[index.html]`

```typescript

<!DOCTYPE html>
<html lang="en">

    <head>
    <title>Essential JS 2 In-place Editor</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Typescript In-place Editor Control">
    <meta name="author" content="Syncfusion">
    <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-data/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-inplace-editor/styles/material.css" rel="stylesheet" type="text/css" />

    <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js"
        type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js"
        type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js"
        type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js"
        type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js"
        type="text/javascript"></script>
        <script src="https://cdn.syncfusion.com/ej2/ej2-inplace-editor/dist/global/ej2-inplace-editor.min.js"
        type="text/javascript"></script>
</head>
<body>
   <div id="element"></div>
   <script>
    var data = ['Australia', 'Bermuda', 'Canada', 'Cameroon', 'Denmark', 'Finland', 'Greenland', 'Poland'];
    var editObj = new ej.inplaceeditor.InPlaceEditor({
    type: 'DropDownList',
    model: {
        dataSource: data,
        placeholder: 'Select Country'
      }
    });
    editObj.appendTo('#element');
</script>
</body>
</html>

```

## Integrate DatePicker

You can render the Essential JS2 [DatePicker](../api/datepicker) by changing the [`type`](../api/inplace-editor/inputType/) property as [`Date`](../api/inplace-editor/inputType/)  and also configure its properties and methods using the [`model`](../api/inplace-editor/#model) property.

In the following sample, [`type`](../api/inplace-editor/inputType/) and [`model`](../api/inplace-editor/#model) values are configured to render the [DatePicker](../api/datepicker) control.

`[index.html]`

```typescript

<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 In-place Editor</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Typescript In-place Editor Control">
    <meta name="author" content="Syncfusion">
    <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-data/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-inplace-editor/styles/material.css" rel="stylesheet" type="text/css" />

    <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js"
    type="text/javascript"></script>
    <script src="https://cdn.syncfusion.com/ej2/ej2-inplace-editor/dist/global/ej2-inplace-editor.min.js"
    type="text/javascript"></script>
</head>
<body>
    <div id="element"></div>
    <script>
    var editObj = new ej.inplaceeditor.InPlaceEditor({
      type: 'Date',
      value: new Date('04/12/2018'),
      model: {
          showTodayButton: true
      }
  });
  editObj.appendTo('#element');
</script>
</body>
</html>

```

{% tab template="in-place-editor/getting-started-form", isDefaultActive=true, sourceFiles="index.ts,index.html" es5Template="es5-getting-started"  %}

```typescript

var genderData = ['Male', 'Female'];
var editObj = new ej2_inplace_editor_1.InPlaceEditor({
    type: 'Date',
    mode: 'Inline',
    value: new Date('04/12/2018'),
    model: {
        showTodayButton: true,
        placeholder: 'Select date of birth'
    }
});
editObj.appendTo('#dateofbirth');
var editObj = new ej2_inplace_editor_1.InPlaceEditor({
    value: 'Andrew',
    mode: 'Inline',
    model: {
        placeholder: 'Enter your name'
    }
});
editObj.appendTo('#element');
var editObj = new ej2_inplace_editor_1.InPlaceEditor({
    type: 'DropDownList',
    value: 'Male',
    mode: 'Inline',
    model: {
        dataSource: genderData,
        placeholder: 'Select gender'
    }
});
editObj.appendTo('#gender');

```

{% endtab %}

## Submitting data to the server (save)

You can submit editor value to the server by configuring the [`url`](../api/inplace-editor/#url), [`adaptor`](../api/inplace-editor/adaptorType/) and [`primaryKey`](../api/inplace-editor/#primarykey) property.

| Property   | Usage                                           |
|------------|---------------------------------------------------------|
| **`url`**        | Gets the URl for server submit action.        |
| **`adaptor`**    | Specifies the adaptor type that is used by DataManager to communicate with DataSource.                |
| **`primaryKey`** | Defines the unique primary key of editable field which can be used for saving data in the data-base.|

> The [`primaryKey`](../api/inplace-editor/#primarykey) property is mandatory. If it's not set, edited data are not sent to the server.

## Refresh In-place Editor with modified value

The edited data is submitted to the server and you can see the new values getting reflected in the In-place Editor.

{% tab template="in-place-editor/getting-started", sourceFiles="index.ts,index.html" es5Template="getting-started" %}

```typescript

import { InPlaceEditor, ActionEventArgs, MultiSelect } from '@syncfusion/ej2-inplace-editor';
InPlaceEditor.Inject(MultiSelect);
let serviceUrl: string = 'https://ej2services.syncfusion.com/development/web-services/api/Editor/UpdateData';
let frameWorkList: string[] = ['Andrew Fuller', 'Janet Leverling', 'Laura Callahan', 'Margaret Hamilt', 'Michael Suyama', 'Nancy Davloio', 'Robert King'];
let newEle: HTMLElement = document.getElementById('newValue');
let oldEle: HTMLElement = document.getElementById('oldValue');
let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DropDownList',
    value: 'Andrew Fuller',
    name: 'Employee',
    url: serviceUrl,
    primaryKey: "Employee",
    adaptor: 'UrlAdaptor',
    actionSuccess: function(e) {
      oldEle.textContent = newEle.textContent;
      newEle.textContent = e.value;
    },
    model: {
        dataSource: frameWorkList,
        popupHeight: '200px',
        placeholder: 'Select employee'
    }
});
editObj.appendTo('#element');

```

{% endtab %}

## See Also

* [Types of rendering the editor](./integration/)