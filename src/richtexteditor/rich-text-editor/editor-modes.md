---
title: "Rich text editor Editor modes"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the markdown editing and HTML editing of the content through out the page."
---

# Editor modes

The Rich Text Editor component used to create and edit the content and return valid HTML markup or markdown (MD) of the content. It supports the following two editing formation.

* HTML Editor
* Markdown Editor

## HTML editor

Rich Text Editor is a WYSIWYG editing control for formatting the word content as HTML.

The HTML editing mode is the default mode in Rich Text Editor to format the content through the available toolbar items to return the valid HTML markup. Set the [editorMode](../api/rich-text-editor/#editormode) property as `HTML`.

> To create Rich Text Editor with HTML editing feature, inject the [htmleditor](../api/rich-text-editor/#htmleditor) module to the Rich Text Editor using the `RichTextEditor.Inject(HtmlEditor)` method.

{% tab template="rich-text-editor/getting-started", es5Template="html-editor" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor);

// initialize RichTextEditor component
let defaultRTE: RichTextEditor = new RichTextEditor({
    value: `<p>The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content.Users can format their content using standard toolbar commands.</p>
    <p><b>Key features:</b></p>
    <ul><li><p>Provides <b>IFRAME</b> and <b>DIV</b> modes</p></li>
    <li><p>Capable of handling markdown editing.</p></li>
    <li><p>Contains a modular library to load the necessary functionality on demand.</p></li>
    <li><p>Provides a fully customizable toolbar.</p></li>
    <li><p>Supports third-party library integration.</p></li>
    </ul>`
});
// render initialized Rich Text Editor
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Markdown editor

Set the [`editorMode`](../api/rich-text-editor/#editormode) property as `Markdown` to create or edit the content and apply formatting to view markdown formatted content.

The third-party library such as `Marked` or any other library is used to convert markdown into HTML content.

* The Supported Tags are  `h6`,`h5`,`h4`,`h3`,`h2`,`h1`,`blockquote`,`pre`,`p`,`OL`,`UL`.
* The Supported Selection Tags are `Bold`, `Italic`, `StrikeThrough`, `InlineCode`, `SubScript`, `SuperScript`, `UpperCase`, `LowerCase`.

{% tab template="rich-text-editor/getting-started", es5Template="markdown-editor" %}

```typescript

import { RichTextEditor, Toolbar, MarkdownEditor } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, MarkdownEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
  value: `***Overview***
  The Rich Text Editor component is WYSIWYG ("what you see is what you get") editor used to create and edit the content and return valid HTML markup or markdown (MD) of the content. The editor provides a standard toolbar to format content using its commands. Modular library features to load the necessary functionality on demand. The toolbar contains commands to align the text, insert link, insert image, insert list, undo/redo operation, HTML view, and more.

  ***Key features***
  - *Mode*: Provides IFRAME and DIV mode.
  - *Module*: Modular library to load the necessary functionality on demand.
  - *Toolbar*: Provide a fully customizable toolbar.
  - *Editing*: HTML view to edit the source directly for developers.
  - *Third-party Integration*: Supports to integrate third-party library.
  - *Preview*: Preview the modified content before saving it.
  - *Tools*: Handling images, hyperlinks, video, uploads and more.
  - *Undo and Redo*: Undo/redo manager.
  - *Lists*:Creates bulleted and numbered list.`,
  editorMode: 'Markdown',
 });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

> To create Rich Text Editor with Markdown editing feature, inject the [`MarkdownEditor`](../api/rich-text-editor/markdownEditor/#markdowneditor) module to the Rich Text Editor using the `RichTextEditor.Inject(MarkdownEditor)` method.

For further details on Markdown editing, refer to the [`Markdown`](./markdown/) section.

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to render the iframe](./iframe/)