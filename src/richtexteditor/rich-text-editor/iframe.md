---
title: "Rich text editor Iframe mode"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control demonstrates the default rendering of the Rich Text Editor in iframe mode."
---

# Iframe

When the [`iframeSettings`](../api/rich-text-editor/#iframesettings) option is enabled, the Rich Text Editor creates the iframe element as the content area on control initialization; it is used to display and editing the content. In Content area, the editor displays only the body tag of a `<iframe>` document.

{% tab template="rich-text-editor/iframe", es5Template="getting-started" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

// initialize Rich Text Editor component
let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    iframeSettings: {
        enable: true
    }
});
// render initialized Rich Text Editor
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## IFrame attributes

The editor allows you to pass an additional attribute to body tag of a `<iframe>` element using [`attributes`](../api/rich-text-editor/iFrameSettings/#attributes) fields of [`iframeSettings`](../api/rich-text-editor/#iframesettings) property. The property contains name/value pairs in string format. It is used to override the default appearance of the content area.

{% tab template="rich-text-editor/iframe", es5Template="attribute" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

// initialize Rich Text Editor component
let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    iframeSettings: {
        enable: true,
        attributes: {
            readonly: 'readonly'
        }
    }
});
// render initialized Rich Text Editor
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Adding external CSS/Script File

The editor offers you to add external CSS file to style the `<iframe>` element. Easily change the appearance of editor’s content using an external CSS file using [`styles`](../api/rich-text-editor/resources/#styles) field in [`iframeSettings`](../api/rich-text-editor/#iframesettings) property.

Likewise, add the external script file to the `<iframe>` element using [`scripts`](../api/rich-text-editor/resources/#scripts) field of [`iframeSettings`](../api/rich-text-editor/#iframesettings) to provide the additional functionalities to the Rich Text Editor.

{% tab template="rich-text-editor/iframe", es5Template="resource" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

// initialize Rich Text Editor component
let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    iframeSettings: {
        enable: true,
        attributes: {
            readonly: 'readonly'
        },
        resources: {
            scripts: ['my-script.js'],
            styles: ['my-style.css']
        }
    }
});
// render initialized Rich Text Editor
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## See Also

* [How to change the editor mode](./editor-modes/#markdown-editor)