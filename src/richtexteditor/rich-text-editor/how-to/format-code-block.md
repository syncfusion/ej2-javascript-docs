---
title: " Rich Text Editor how to format code block using toolbar button"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains about how to format code block using toolbar button."
---

# Format code block using toolbar button

You can configure code block formatting as a separate toolbar button by adding the **InsertCode** keyword within the [toolbarSettings](./../../api/rich-text-editor/toolbarSettings/#toolbarsettings) items property.

The InsertCode button has a toggle state to apply code block formatting to the editor and remove code block formatting from the editor.

The following sample demonstrates how to config the InsertCode button in toolbar and set the background color to “pre” tag for highlighting the code block.

{% tab template="rich-text-editor/how-to-format-code", es5Template="format-code-block" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
  toolbarSettings: {
    items: ['InsertCode']
  }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}