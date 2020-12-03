---
title: "Rich text editor Getting started"
component: "Rich Text Editor"
description: "This section explains how to create a simple Syncfusion JavaScript (ECMAScript5) Rich Text Editor control and configure its functionalities."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-richtexteditor/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Rich Text Editor</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Rich Text Editor's global script -->
            <script src="resources/ej2-richtexteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `textarea` element and initiate the `Essential JS 2 Rich Text Editor` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Rich Text Editor</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Rich Text Editor's global script -->
            <script src="resources/ej2-richtexteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--Element which will render as RTE-->
     <textarea id="defaultRTE">
     </textarea>
            <script>
                // initialize Rich Text Editor component
               var RichTextEditor = new ej.richtexteditor.RichTextEditor();
                // Render initialized Rich Text Editor.
                RichTextEditor.appendTo('#defaultRTE');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Rich Text Editor** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js`](http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `textarea` element and initiate the `Essential JS 2 Rich Text Editor` component in the index.html by using following code.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Rich Text Editor</title>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Rich Text Editor's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!--Element which will render as RTE-->
     <textarea id="defaultRTE">
     </textarea>
            <script>
                // initialize Rich Text Editor component
               var RichTextEditor = new ej.richtexteditor.RichTextEditor();
                // Render initialized Rich Text Editor.
                RichTextEditor.appendTo('#defaultRTE')
            </script>
       </body>
  </html>

```

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Rich Text Editor` component.

### Initialize from textarea

Initialize the Rich Text Editor on a textarea.

Now, add an HTML textarea element to act as the Rich Text Editor element in `index.html` using the following code.

`[src/index.html]`

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
      <head>
          <title>Essential JS 2</title>
          <!-- Essential JS 2 material theme -->
          <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
          <!-- Essential JS 2 Rich Text Editor's global script -->
          <script src="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js" type="text/javascript"></script>
      </head>
      <body>
          <!--Element which will render as RTE-->
    <textarea id="defaultRTE"></textarea>
  </body>
</html>

```

Place the following Rich Text Editor code in the `index.js` file.

`[src/index.js]`

```javascript
// initialize Rich Text Editor component
var defaultRTE = new ej.richtexteditor.RichTextEditor({});

// render initialized Rich Text Editor
defaultRTE.appendTo("#defaultRTE");

```

Output will be displayed as follows

{% tab template="rich-text-editor/text-area-sample", es5Template="getting-started" %}

```typescript
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

// initialize Rich Text Editor component
let defaultRTE: RichTextEditor = new RichTextEditor({ });
// render initialized Rich Text Editor
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

### Initialize from `<div>` element

Rich Text Editor can be initialized on div element as shown below

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Essential JS 2 Rich Text Editor</title>
      <!-- Essential JS 2 material theme -->
      <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
      <!-- Essential JS 2 Rich Text Editor's global script -->
      <script src="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js" type="text/javascript"></script>
</head>

<body>
    <!--Element which will render as RTE-->
     <div id="defaultRTE">
       <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
      <p><b>Key features:</b></p>
        <ul><li><p>Provides IFRAME and DIV modes</p></li>
        <li><p>Capable of handling markdown editing.</p></li>
        <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
        <li><p>Provides a fully customizable toolbar.</p></li>
        <li><p>Provides HTML view to edit the source directly for developers.</p></li>
        <li><p>Supports third-party library integration.</p></li>
        <li><p>Allows preview of modified content before saving it.</p></li>
        <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
        </ul>
     </div>
     <script>
        // initialize Rich Text Editor component
        var RichTextEditor = new ej.richtexteditor.RichTextEditor({
          height: '340px'
        });
        // Render initialized Rich Text Editor.
        RichTextEditor.appendTo('#defaultRTE')
    </script>
</body>
</html>
```

### Initialize from `<IFRAME>` element

The Rich Text Editor’s content is placed in an iframe and isolated from the rest of the page.

Initialize the Rich Text Editor on div element and set the `enable` field of [iframeSettings](../api/rich-text-editor/iFrameSettings/#iframesettings) property to true.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2 Rich Text Editor</title>
      <!-- Essential JS 2 material theme -->
      <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
      <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
      <!-- Essential JS 2 Rich Text Editor's global script -->
      <script src="http://cdn.syncfusion.com/ej2/ej2-richtexteditor/dist/global/ej2-richtexteditor.min.js" type="text/javascript"></script>
</head>

<body>
    <!--Element which will render as RTE-->
     <div id="defaultRTE">
       <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
      <p><b>Key features:</b></p>
        <ul><li><p>Provides IFRAME and DIV modes</p></li>
        <li><p>Capable of handling markdown editing.</p></li>
        <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
        <li><p>Provides a fully customizable toolbar.</p></li>
        <li><p>Provides HTML view to edit the source directly for developers.</p></li>
        <li><p>Supports third-party library integration.</p></li>
        <li><p>Allows preview of modified content before saving it.</p></li>
        <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
        </ul>
     </div>
     <script>
        // initialize Rich Text Editor component
        var RichTextEditor = new ej.richtexteditor.RichTextEditor({
          height: '340px',
          iframeSettings: {
                enable: true
            }});
        // Render initialized Rich Text Editor.
        RichTextEditor.appendTo('#defaultRTE')
    </script>
</body>
</html>

```

## Module Injection

To create Rich Text Editor with additional features, inject the required modules. The following modules are used to extend Rich Text Editor’s basic functionality.

* `toolbar` - Inject this module to use Toolbar feature.
* `link` - Inject this module to use link in Rich Text Editor feature.
* `image`- Inject this module to use image in Rich Text Editor feature.
* `count` - Inject this module to use character count in Rich Text Editor.
* `markdownEditor`-Inject this module to use Rich Text Editor as markdown editor.
* `htmlEditor` - Inject this module to use Rich Text Editor as html editor.
* `quickToolbar` - Inject this module to use quick toolbar feature for the target element.

These modules should be injected into the Rich Text Editor using the `RichTextEditor.Inject` method.

## Configure the Toolbar

Configure the toolbar with the tools using items field of the [toolbarSettings](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property as your application requires.

{% tab template="rich-text-editor/getting-started", es5Template="getting-started" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
  toolbarSettings: {
      items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
        'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
        'LowerCase', 'UpperCase', '|',
        'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
        'Outdent', 'Indent', '|',
        'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
        'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
    }});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

> `|` and `-` can insert a vertical and horizontal separator lines in the toolbar.

## Insert images and links

The [`image`](../api/rich-text-editor/image/#image) module inserts an image into Rich Text Editor’s content area, and the [`link`](../api/rich-text-editor/link/#link) module links external resources such as website URLs, to selected text in the Rich Text Editor’s content, respectively.

The link inject module adds a link icon to the toolbar and the image inject module adds an image icon to the toolbar.

Specifies the items to be rendered in the quick toolbar based on the target element such image, link and text element. The quick toolbar opens to customize the element by clicking the target element.

{% tab template="rich-text-editor/getting-started", es5Template="image-basic" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
  height: 340,
  quickToolbarSettings: {
      image: [
        'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'OpenImageLink', '-',
        'EditImageLink', 'RemoveImageLink', 'Display', 'AltText', 'Dimension'
      ]
    },
  toolbarSettings: {
      items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
        'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
        'LowerCase', 'UpperCase', '|',
        'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
        'Outdent', 'Indent', '|',
        'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
        'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
    }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Retrieve the formatted content

To retrieve the editor contents, use [`value`](../api/rich-text-editor/#value) property of Rich Text Editor.

```typescript
  var rteValue = defaultRTE.value;
```

Or, you can use the public method, [`getHtml`](../api/rich-text-editor/#gethtml) to retrieve the Rich Text Editor content.

```typescript
  var rteValue = defaultRTE.getHtml();
```

To fetch the Rich Text Editor's text content, use [`getText`](../api/rich-text-editor/#gettext) method of Rich Text Editor.

```typescript
  var rteValue = defaultRTE.getText();
```

## See Also

* [How to change the editor type](./editor-modes/)
* [How to render the iframe](./iframe/)
* [How to render the toolbar in inline mode](./inline-mode/)