---
title: "Rich text editor Styling"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to format text, paragraphs, characters with the toolbar items."
---

# Styling

## Font name and size

By default, the editor is initialized with font name and  font size as **null**. To change it, select a different font name and font size from the drop-down in the editor’s toolbar.

To apply different font style for section of the content, select the text that you would like to change, and select a required font style from the drop-down to apply the changes to the selected text.

### FontName DropDowns

The following table list the default font name and width of the [fontname](../api/rich-text-editor/fontFamily/#fontfamily) dropdown and available list of font names.

| Default Key | Default Value |
|----------------|--------------------------------------|
| font name | null |
|width | 65px|
| items | { text: 'Segoe UI', value: 'Segoe UI' },{ text: 'Arial', value: 'Arial,Helvetica,sans-serif' },{ text: 'Courier New', value: 'Courier New,Courier,monospace' },{ text: 'Georgia', value: 'Georgia,serif' },{ text: 'Impact', value: 'Impact,Charcoal,sans-serif' },{ text: 'Lucida Console', value: 'Lucida Console,Monaco,monospace' },{ text: 'Tahoma', value: 'Tahoma,Geneva,sans-serif' },{ text: 'Times New Roman', value: 'Times New Roman,Times,serif' },{ text: 'Trebuchet MS', value: 'Trebuchet MS,Helvetica,sans-serif' },{ text: 'Verdana', value: 'Verdana,Geneva,sans-serif' }|

### FontSize DropDowns

The following table list the default font size and width of the [fontsize](../api/rich-text-editor/fontSize/#fontsize) dropdown and available list of font size.

| Default Key | Default Value |
|----------------|---------|
| font size | null |
| width | 35px.|
| items |{ text: '8', value: '8pt' },{ text: '10', value: '10pt' },{ text: '12', value: '12pt' },{ text: '14', value: '14pt' },{ text: '18', value: '18pt' },{ text: '24', value: '24pt' },{ text: '36', value: '36pt' }.|

The following sample demonstrates the option to add the font name and font size tools to the toolbar as well as modify the default [width](../api/rich-text-editor/fontSize/#width) of the tools.

{% tab template="rich-text-editor/styling", es5Template="font-name" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);


let defaultRTE: RichTextEditor = new RichTextEditor({
  height: 340,
  toolbarSettings: {
        items: [ 'FontName', 'FontSize']
    },
    fontSize: {
        width: '40px'
    },
    fontFamily: {
        width: '60px'
    }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Custom font and size

Rich Text Editor support to provide custom fonts and size with existing list.
If you want to add additional font names and font sizes to font drop-down, pass the font information as JSON data to the items field of [fontsize](../api/rich-text-editor/fontSize/#fontsize) and [fontFamily](../api/rich-text-editor/fontFamily/#fontfamily) property.

{% tab template="rich-text-editor/styling", es5Template="custom-size" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Image,  Link, HtmlEditor, QuickToolbar, NodeSelection } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Image,  Link, HtmlEditor, QuickToolbar );

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    toolbarSettings: {
        items: [ 'FontName', 'FontSize']
    },
    fontSize: {
        width: '40px',
        items: [{ text: '8 pt', value: '8pt' },
        { text: '10 pt', value: '10pt' },
        { text: '12 pt', value: '12pt' },
        { text: '14 pt', value: '14pt' },
        { text: '42 pt', value: '42pt' }]
    },
    fontFamily: {
        width: '60px',
        items: [
        { text: 'Segoe UI', value: 'Segoe UI' },
        { text: 'Arial', value: 'Arial,Helvetica,sans-serif' },
        { text: 'Courier New', value: 'Courier New,Courier,monospace' },
        { text: 'Georgia', value: 'Georgia,serif' },
        { text: 'Impact', value: 'Impact,Charcoal,sans-serif' },
        { text: 'Calibri Light', value: 'CalibriLight' }]
    }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Font and Background color

To apply font color or background color for a selected content of Rich Text Editor, use font color and background color tools.

Rich Text Editor support to provide customs font color and background color with existing list through the [`colorCode`](../api/rich-text-editor/backgroundColor/#colorcode) field of [`fontColor`](../api/rich-text-editor/fontColor/#fontcolor) and [`backgroundColor`](../api/rich-text-editor/backgroundColor/#backgroundcolor).

The FontColor and BackgroundColor property has two [mode](../api/rich-text-editor/backgroundColor/#mode) Picker and Palette. Palette mode has predefined set of [colorCode](../api/rich-text-editor/backgroundColor/#colorcode) and in the picker mode, more colors has been provided. Through [`modeSwitcher`](../api/rich-text-editor/backgroundColor/#modeswitcher), you can able to switch between these two options.

{% tab template="rich-text-editor/styling", es5Template="font-color" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
  height: 340,
  toolbarSettings: {
    items: [ 'FontColor', 'BackgroundColor']
  },
  backgroundColor: {
      modeSwitcher : true
  },
  fontColor: {
      modeSwitcher : true
  }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Editor content styles

By default, The content styles of Rich Text Editor are not returned while retrieving HTML value from the editor. So, the styles are not applied when using the HTML value outside of the editor. To get the styles to Rich Text Editor’s content for your application, You can copy and use the below styles directly in your application. The styles listed below which used in the UI elements of the Rich Text Editor.  

> Make sure to add a CSS class ‘e-rte-content’ to the content container.

```css

.e-rte-content p {
  margin: 0 0 10px;
  margin-bottom: 10px;
}

.e-rte-content li {
  margin-bottom: 10px;
}

.e-rte-content h1 {
  font-size: 2.17em;
  font-weight: 400;
  line-height: 1;
  margin: 10px 0;
}

.e-rte-content h2 {
  font-size: 1.74em;
  font-weight: 400;
  margin: 10px 0;
}

.e-rte-content h3 {
  font-size: 1.31em;
  font-weight: 400;
  margin: 10px 0;
}

.e-rte-content h4 {
  font-size: 1em;
  font-weight: 400;
  margin: 0;
}

.e-rte-content h5 {
  font-size: 00.8em;
  font-weight: 400;
  margin: 0;
}

.e-rte-content h6 {
  font-size: 00.65em;
  font-weight: 400;
  margin: 0;
}

.e-rte-content blockquote {
  margin: 10px 0;
  margin-left: 0;
  padding-left: 5px;
}

.e-rte-content pre {
  background-color: inherit;
  border: 0;
  border-radius: 0;
  color: #333;
  font-size: inherit;
  line-height: inherit;
  margin: 0 0 10px;
  overflow: visible;
  padding: 0;
  white-space: pre-wrap;
  word-break: inherit;
  word-wrap: break-word;
}

.e-rte-content strong, .e-rte-content b {
  font-weight: 700;
}

.e-rte-content a {
  text-decoration: none;
  -webkit-user-select: auto;
  -ms-user-select: auto;
  user-select: auto;
}

.e-rte-content a:hover {
  text-decoration: underline;
}

.e-rte-content h3 + h4,
.e-rte-content h4 + h5,
.e-rte-content h5 + h6 {
  margin-top: 00.6em;
}

.e-rte-content .e-rte-image.e-imgbreak {
  border: 0;
  cursor: pointer;
  display: block;
  float: none;
  margin: 5px auto;
  max-width: 100%;
  position: relative;
}

.e-rte-content .e-rte-image {
  border: 0;
  cursor: pointer;
  display: block;
  float: none;
  margin: auto;
  max-width: 100%;
  position: relative;
}

.e-rte-content .e-rte-image.e-imginline {
  display: inline-block;
  float: none;
  margin-left: 5px;
  margin-right: 5px;
  max-width: calc(100% - (2 * 5px));
  vertical-align: bottom;
}

.e-rte-content .e-rte-image.e-imgcenter {
  cursor: pointer;
  display: block;
  float: none;
  margin: 5px auto;
  max-width: 100%;
  position: relative;
}

.e-rte-content .e-rte-image.e-imgleft {
  float: left;
  margin: 0 5px 0 0;
  text-align: left;
}

.e-rte-content .e-rte-image.e-imgright {
  float: right;
  margin: 0 0 0 5px;
  text-align: right;
}

.e-rte-content .e-rte-img-caption {
  display: inline-block;
  margin: 5px auto;
  max-width: 100%;
  position: relative;
}

.e-rte-content .e-rte-img-caption.e-caption-inline {
  display: inline-block;
  margin: 5px auto;
  margin-left: 5px;
  margin-right: 5px;
  max-width: calc(100% - (2 * 5px));
  position: relative;
  text-align: center;
  vertical-align: bottom;
}

.e-rte-content .e-rte-img-caption.e-imgcenter {
  display: block;
}

.e-rte-content .e-rte-img-caption .e-rte-image.e-imgright,
.e-rte-content .e-rte-img-caption .e-rte-image.e-imgleft {
  float: none;
  margin: 0;
}

.e-rte-content .e-rte-table {
  border-collapse: collapse;
  empty-cells: show;
}

.e-rte-content .e-rte-table td,
.e-rte-content .e-rte-table th {
  border: 1px solid #bdbdbd;
  height: 20px;
  min-width: 20px;
  padding: 2px 5px;
  vertical-align: middle;
}

.e-rte-content .e-rte-table.e-dashed-border td,
.e-rte-content .e-rte-table.e-dashed-border th {
  border-style: dashed;
}

.e-rte-content .e-rte-img-caption .e-img-inner {
  box-sizing: border-box;
  display: block;
  font-size: 16px;
  font-weight: initial;
  margin: auto;
  opacity: .9;
  position: relative;
  text-align: center;
  width: 100%;
}

.e-rte-content .e-rte-img-caption .e-img-wrap {
  display: inline-block;
  margin: auto;
  padding: 0;
  width: 100%;
}

.e-rte-content blockquote {
  border-left: solid 2px #333;
}

.e-rte-content a {
  color: #2e2ef1;
}

.e-rte-content .e-rte-table th {
  background-color: #e0e0e0;
}

```

## See Also

* [How to add google fonts to the font family](./how-to/add-google-font/)
* [How to customize the toolbar items shortcut key](./how-to/shortcut-key/)
* [How to customize the placeholder](./how-to/placeholder/)
* [How to change the default font family](./how-to/default-font/)