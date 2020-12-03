---
title: "Rich text editor changing the default font family"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to change the default `fontFamily`."
---

# Change default font-family

By using [`default`](../../api/rich-text-editor/#fontfamily) property, you can change the default font-family of the Rich Text Editor. To change the font-family of the Rich Text Editor content while loading, we need to give the font-family in the style section with the help of [`cssClass`](../../api/rich-text-editor/#cssclass) property.

{% tab template="rich-text-editor/how-to-default-font", es5Template="default-font", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
   fontFamily: {
        default:"Noto Sans", // to define default font-family
        items:[
          {text: "Segoe UI", value: "Segoe UI", class: "e-segoe-ui",  command: "Font", subCommand: "FontName"},
          {text: "Noto Sans", value: "Noto Sans",  command: "Font", subCommand: "FontName"},
          {text: "Impact", value: "Impact,Charcoal,sans-serif", class: "e-impact", command: "Font", subCommand: "FontName"},
          {text: "Tahoma", value: "Tahoma,Geneva,sans-serif", class: "e-tahoma", command: "Font", subCommand: "FontName"},
        ]
      },
        toolbarSettings: {
            items: ['Bold', 'Italic', 'Underline', 'StrikeThrough','|',
                'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
                'LowerCase', 'UpperCase', '|',
                'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
                'Outdent', 'Indent', '|',
                'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
                'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
        },
        cssClass: "customClass"
    });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}