---
title: "Rich text editor Shortcut keys"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the customization of shortcut keys."
---

# Customize shortcut keys

It can be achieved by using [`formatter`](../../api/rich-text-editor/#formatter) property. We need to create `customformatterModel` to configure the `keyConfig` using `IHtmlFormatterModel` class and assign the same to the formatter property. Here, `ctrl+q` is configured to open the `Insert Hyperlink` dialog.

{% tab template="rich-text-editor/how-to", es5Template="custom-key", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, IHtmlFormatterModel, HTMLFormatter, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let customHTMLModel: IHtmlFormatterModel = { // formatter is used to configure the custom key
    keyConfig: {
        'insert-link': 'ctrl+q', // configure the desired key
    }
};

let defaultRTE: RichTextEditor = new RichTextEditor({
    formatter: new HTMLFormatter(customHTMLModel), // to configure custom key
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

> We need to import `IHtmlFormatterModel` and `HTMLFormatter` to configure the shortcut key.
