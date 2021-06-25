---
title: "Rich text editor Toolbar configuration"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the toolbar which provides a set of commands for editing and formatting the content."
---

# Toolbar

The Rich Text Editor toolbar contains a collection of tools such as bold, italic, and text alignment buttons that are used to format the content. However, in most integrations, you can customize the toolbar configurations easily to suit your needs.

To create Rich Text Editor with Markdown editing feature, inject the [`Toolbar`](../api/rich-text-editor/toolbar/#toolbar) module to the Rich Text Editor using the `RichTextEditor.Inject(Toolbar)` method.

The Rich Text Editor allows you to configure different types of toolbar using [`toolbarSettings.type`](../api/rich-text-editor/toolbarType/#toolbartype) property. The types of toolbar are:

1. Expand
2. MultiRow

## Expand Toolbar

The default mode of [`toolbarSettings.type`](../api/rich-text-editor/toolbarType/#toolbartype) it will hide the overflowing items in the next row. By clicking the expand arrow, view the overflowing toolbar items.

{% tab template="rich-text-editor/toolbar", es5Template="expand" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    value: ` <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
        <p><b>Key features:</b></p>
            <ul><li><p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p></li>
            <li><p>Capable of handling markdown editing.</p></li>
            <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
            <li><p>Provides a fully customizable toolbar.</p></li>
            <li><p>Provides HTML view to edit the source directly for developers.</p></li>
            <li><p>Supports third-party library integration.</p></li>
            <li><p>Allows preview of modified content before saving it.</p></li>
            <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
            </ul>`,
    toolbarSettings: {
        type: 'Expand'
    }});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Multi-row Toolbar

Set the type as MultiRow in [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) to hide the overflowing items in the next row. All toolbar items are visible.

{% tab template="rich-text-editor/toolbar", es5Template="multirow" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
  height: 340,
  value: ` <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
      <p><b>Key features:</b></p>
        <ul><li><p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p></li>
        <li><p>Capable of handling markdown editing.</p></li>
        <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
        <li><p>Provides a fully customizable toolbar.</p></li>
        <li><p>Provides HTML view to edit the source directly for developers.</p></li>
        <li><p>Supports third-party library integration.</p></li>
        <li><p>Allows preview of modified content before saving it.</p></li>
        <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
        <li><p>Contains undo/redo manager.</p></li>
        <li><p>Creates bulleted and numbered lists.</p></li>
        </ul>`,
  toolbarSettings: {
    type: 'MultiRow'
  }});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Floating Toolbar

By default, toolbar is float at the top of the Rich Text Editor on scrolling. It can be customized by specifying the offset of the floating toolbar from documents top position using  [`floatingToolbarOffset`](../api/rich-text-editor/#floatingtoolbaroffset).

Enable or disable the floating toolbar using [`enableFloating`](../api/rich-text-editor/toolbarSettings/#enablefloating) of the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property.

{% tab template="rich-text-editor/floating-toolbar", es5Template="floating" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
   height: 340,
   toolbarSettings: {
      enableFloating: false
   },
   value: ` <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul><li><p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p></li>
    <li><p>Capable of handling markdown editing.</p></li>
    <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
    <li><p>Provides a fully customizable toolbar.</p></li>
    <li><p>Provides HTML view to edit the source directly for developers.</p></li>
    <li><p>Supports third-party library integration.</p></li>
    <li><p>Allows preview of modified content before saving it.</p></li>
    <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
    </ul>`});
defaultRTE.appendTo('#defaultRTE');

let float: CheckBox = new CheckBox({
    // set false for enable the checked state at initial rendering
    checked: false,
    label: 'Enable Floating',
    // bind change event
    change: (args: ChangeEventArgs) => {
        defaultRTE.toolbarSettings.enableFloating = (args as any).checked;
        defaultRTE.dataBind();
    }
});
float.appendTo('#float');

```

{% endtab %}

## Toolbar items

The following table lists the tools available in the toolbar.

| Name | Summary | Initialization |
|----------------|---------|------------------------------------------|
| Undo | Allows to undo the actions.|toolbarSettings: { items: ['Undo']} |
| Redo | Allows to redo the actions.|toolbarSettings: { items: ['Redo']}|
| Alignment | Align the content with left, center, and right margin.|toolbarSettings: { items: ['Alignments']}|
| OrderedList | Create a new list item(numbered). |toolbarSettings: { items: ['OrderedList']}|
| UnorderedList | Create a new list item(bulleted). |toolbarSettings: { items: ['UnorderedList']}|
| Indent | Allows to increase the indent level of the content.|toolbarSettings: { items: ['Indent']}|
| Outdent | Allows to decrease the indent level of the content.|toolbarSettings: { items: ['Outdent']}|
| Hyperlink | Creates a hyperlink to a text or image to a specific location in the content.|toolbarSettings: { items: ['CreateLink']}|
| Images | Inserts an image from an online source or local computer. |toolbarSettings: { items: ['Image']}|
| LowerCase | Change the case of selected text to lower in the content. |toolbarSettings: { items: ['LowerCase']}|
| UpperCase | Change the case of selected text to upper  in the content.|toolbarSettings: { items: ['UpperCase’']}|
| SubScript | Makes the selected text as subscript (lower).|toolbarSettings: { items: ['SubScript']}|
| SuperScript | Makes the selected text as superscript (higher).|toolbarSettings: { items: ['SuperScript’']}|
| Print | Allows to print the editor content. |toolbarSettings: { items: ['Print']}|
| FontName | Defines the fonts that appear under the Font Family DropDownList from the Rich Text Editor's toolbar. |toolbarSettings: { items: ['FontName']}|
| FontSize | Defines the font sizes that appear under the Font Size DropDownList from the Rich Text Editor's toolbar.|toolbarSettings: { items: ['FontSize']}|
| FontColor | Specifies an array of colors can be used in the colors popup for font color.|toolbarSettings: { items: ['FontColor']}|
| BackgroundColor | Specifies an array of colors can be used in the colors popup for background color.|toolbarSettings: { items: ['BackgroundColor']}|
| Format | An Object with the options that will appear in the Paragraph Format dropdown from the toolbar. |toolbarSettings: { items: ['Formats']}|
| StrikeThrough | Apply double line strike through formatting for the selected text. |toolbarSettings: { items: ['StrikeThrough']}|
| ClearFormat | The clear format tool is useful to remove all formatting styles (such as bold, italic, underline, color, superscript, subscript, and more) from currently selected text. As a result, all the text formatting will be cleared and return to its default formatting styles.|toolbarSettings: { items: ['ClearFormat']}|
| FullScreen | Stretches the editor to the maximum width and height of the browser window.|toolbarSettings: { items: ['FullScreen']}|
| SourceCode | Rich Text Editor includes the ability for users to directly edit HTML code via “Source View”. If you made any modification in Source view directly, synchronize with Design view.|toolbarSettings: { items: ['SourceCode']}|
| NumberFormatList | Allows to create list items with various list style types(numbered)|toolbarSettings: { items: ['NumberFormatList']}|
| BulletFormatList | Allows to create list items with various list style types(bulleted)|toolbarSettings: { items: ['BulletFormatList']}|

By default, tools will be arranged in following order.

> items: ['Bold', 'Italic', 'Underline', '|', 'Formats', 'Alignments', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', '|', 'SourceCode', 'Undo', 'Redo']

The tools order can be customized as our application requirement. If you are not specifying any tools order, the editor will create the toolbar with default items.

## Custom tool

The Rich Text Editor allows you to configure your own commands to its toolbar using the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property. The command can be plain text, icon, or HTML template. The order and the group can also be defined where the command should be included. Bind the action to the command by getting its instance.

This sample shows how to add your own commands to the toolbar of the Rich Text Editor. The "Ω" command is added to insert special characters in the editor. By clicking the "Ω" command, it will show the special characters list, and then choose the character to be inserted in the editor.

The following code snippet illustrates custom tool with tooltip text which will be included in [`items`](../api/rich-text-editor/toolbarSettings/#items) field of the [`toolbarSettings`](../api/rich-text-editor/toolbarSettings/#toolbarsettings) property.

In the following sample, once Rich Text Editor control is created, the concern event will be [`created`](../api/rich-text-editor/#created) the Dialog component can be rendered and target as RTE content.

```javascript

{
    tooltipText: 'Insert Symbol',
    undo: true,
    click: function() {
    },
    template: '<button class="e-tbar-btn e-btn" tabindex="-1" id="custom_tbar" style="width:100%"><div class="e-tbar-btn-text" style="font-weight: 500;"> &#937;</div></button>'
}

```

Click the `Ω` command to show the special characters list, and then choose the character to be inserted in the editor.

{% tab template="rich-text-editor/custom-tool", es5Template="customtool" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, NodeSelection, Image, QuickToolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';
import { Dialog } from '@syncfusion/ej2-popups';
RichTextEditor.Inject(Toolbar, Link, Image, QuickToolbar, HtmlEditor);
let dialog: Dialog;
let defaultRTE: RichTextEditor = new RichTextEditor({
   height: 340,
   value: ` <p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul><li><p>Provides &lt;IFRAME&gt; and &lt;DIV&gt; modes</p></li>
    <li><p>Capable of handling markdown editing.</p></li>
    <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
    <li><p>Provides a fully customizable toolbar.</p></li>
    <li><p>Provides HTML view to edit the source directly for developers.</p></li>
    <li><p>Supports third-party library integration.</p></li>
    <li><p>Allows preview of modified content before saving it.</p></li>
    <li><p>Handles images, hyperlinks, video, hyperlinks, uploads, etc.</p></li>
    </ul>`,
    toolbarSettings: {
        items: ['Bold', 'Italic', 'Underline', '|', 'Formats', 'Alignments', 'OrderedList',
            'UnorderedList', '|', 'CreateLink', 'Image', '|', 'SourceCode',
            {
                tooltipText: 'Insert Symbol',
                undo: true,
                click: function() {
                    defaultRTE.focusIn();
                    dialog.element.style.display = '';
                    ranges = selection.getRange(document);
                    dialog.width = defaultRTE.element.offsetWidth * 0.5;
                    dialog.dataBind();
                    dialog.show();
                },
                template: '<button class="e-tbar-btn e-btn" tabindex="-1" id="custom_tbar"  style="width:100%"><div class="e-tbar-btn-text" style="font-weight: 500;"> &#937;</div></button>'
            }, '|', 'Undo', 'Redo'
        ]
    },
    created: onCreate
});
defaultRTE.appendTo('#defaultRTE');
let selection: NodeSelection = new NodeSelection();
let ranges: Range;

function onCreate(): void {
  let customBtn: HTMLElement = defaultRTE.element.querySelector('#custom_tbar') as HTMLElement;
  let dialogCtn: HTMLElement = document.getElementById('rteSpecial_char');
  // Initialization of Dialog
  dialog = new Dialog({
      header: 'Special Characters',
      content: dialogCtn,
      target: document.getElementById('container'),
      showCloseIcon: false,
      isModal: true,
      height: 'auto',
      width: '500px',
      overlayClick: dialogOverlay,
      buttons: [{ buttonModel: { content: "Insert", isPrimary: true }, click: onInsert }, { buttonModel: { content: 'Cancel' }, click: dialogOverlay }]
  });
  // Render initialized Dialog
  dialog.appendTo('#customTbarDialog');
  dialog.hide();
  customBtn.onclick = (e: Event) => {
    dialog.element.style.display = '';
    ranges = selection.getRange(document);
    dialog.width = defaultRTE.element.offsetWidth * 0.5;
    dialog.dataBind();
    dialog.show();
    let dialogCtn: HTMLElement = document.getElementById('rteSpecial_char');
    dialogCtn.onclick = (e: Event) => {
        let target: HTMLElement = e.target as HTMLElement;
        let activeEle: HTMLElement = dialog.element.querySelector('.char_block.e-active');
        if (target.classList.contains('char_block')) {
            target.classList.add('e-active');
            if (activeEle) {
                activeEle.classList.remove('e-active');
            }
        }
    };
  }

  function onInsert(): void {
    let activeEle: HTMLElement = dialog.element.querySelector('.char_block.e-active');
    if (activeEle) {
        defaultRTE.executeCommand('insertText', activeEle.textContent , {undo: true});
    }
    dialogOverlay();
  }

  function dialogOverlay(): void {
    let activeEle: HTMLElement = dialog.element.querySelector('.char_block.e-active');
    if (activeEle) {
        activeEle.classList.remove('e-active');
    }
    dialog.hide();
  }
}

```

{% endtab %}

## Quick inline toolbar

Quick commands are opened as context-menu on clicking the corresponding element. The commands must be passed as string collection to image, text, and link attributes of the [`quickToolbarSettings`](../api/rich-text-editor/quickToolbarSettings/#quicktoolbarsettings) property.

| Target Element | Default Quick Toolbar items |
|----------------|---------|
|image | 'Replace', 'Align', 'Caption', 'Remove', 'InsertLink', 'Display', 'AltText','Dimension'.|
| link | 'Open', 'Edit', 'UnLink'.|
| text (`Deprecated`) | 'Cut', 'Copy', 'Paste'.|
| table | 'TableHeader', 'TableRows', 'TableColumns', 'BackgroundColor', 'TableRemove', 'Alignments', 'TableCellVerticalAlign', 'Styles'.|

Custom tool can be added to the corresponding quick toolbar, using [`quickToolbarSettings`](../api/rich-text-editor/quickToolbarSettings/#quicktoolbarsettings) property.

The following sample demonstrates the option to insert the image to the Rich Text Editor content as well as option to rotate the image through the quick toolbar. The image rotation functionalities have been achieved through the [`toolbarClick`](../api/rich-text-editor/#toolbarclick) event.

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

> Rich Text Editor features are segregated into individual feature-wise modules. To use quick toolbar, inject the quick toolbar module using the `RichTextEditor.Inject(Image, Link)`.

## See Also

* [How to render the toolbar in inline mode](./inline-mode/)
* [How to customize the toolbar items shortcut key](./how-to/shortcut-key)