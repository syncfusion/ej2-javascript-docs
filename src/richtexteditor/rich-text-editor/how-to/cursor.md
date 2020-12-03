---
title: "Setting the cursor positon in Rich text editor content"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the addition of Google web fonts to the `fontFamily`."
---

# Set the cursor at the specific range

This can be achieved by using `setRange` method in the Rich Text Editor using `NodeSelection` instance. In this below sample, we have passed the text node (specific location in Rich Text Editor content) in `setStart` method and passed the range in `setRange` method of Rich Text Editor.

{% tab template="rich-text-editor/how-to-cursor", es5Template="cursor", sourceFiles="index.js,index.ts,index.html" %}

```typescript

import { addClass, removeClass, Browser, isNullOrUndefined } from '@syncfusion/ej2-base';
import { RichTextEditor,NodeSelection, Toolbar, Link, Image, Count, HtmlEditor,
  QuickToolbar, ActionBeginEventArgs,IToolsItems } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
   placeholder:'Type Something',
});
defaultRTE.appendTo('#defaultRTE');

document.getElementById('btn').onclick = function(){
  let element: Element= defaultRTE.contentModule.getDocument().getElementById("key");
  let selectioncursor: NodeSelection = new NodeSelection();
  let range: Range = document.createRange();
  range.setStart(element, 1); // to set the range
  selectioncursor.setRange(document, range); // to set the cursor
}

```

{% endtab %}
