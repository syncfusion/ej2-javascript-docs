---
title: " Rich text editor Google Fonts Addition"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the addition of Google web fonts to the `fontFamily`."
---

# Add Google fonts

To use web fonts in Rich Text Editor, it is not needed for the web fonts to be present in local machine. To add the web fonts to Rich Text Editor, we need to refer the web font links and add the font names in the [`fontFamily`](../../api/rich-text-editor/#fontfamily) property.

{% tab template="rich-text-editor/how-to", es5Template="google-web-fonts", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
  RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);
let defaultRTE: RichTextEditor = new RichTextEditor({
      fontFamily: {
        items:[
          {text: "Segoe UI", value: "Segoe UI", class: "e-segoe-ui",  command: "Font", subCommand: "FontName"},
          {text: "Roboto", value: "Roboto",  command: "Font", subCommand: "FontName"},
           // here font is added
          {text: "Great vibes", value: "Great Vibes,cursive",  command: "Font", subCommand: "FontName"},// here font is added
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

    });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

The below font style links are referred in the page.

```typescript

<link rel="stylesheet" href="http://fonts.googleapis.com/css?family=Roboto">
<link rel="stylesheet" href="http://fonts.googleapis.com/css?family=Great+Vibes">

```

> In the above sample, you can see that we have added two Google web fonts (`Roboto` and `Great vibes`) to `Rich Text Editor`.