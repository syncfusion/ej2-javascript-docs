---
title: " Rich text editor placeholder customization"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the customization of placeholder style."
---

# Customize placeholder style

By using `e-rte-placeholder` class, you can customize the placeholder style.

{% tab template="rich-text-editor/how-to-placeholder", es5Template="placeholder", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count);

let defaultRTE: RichTextEditor = new RichTextEditor({ placeholder:'Type Something' });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}