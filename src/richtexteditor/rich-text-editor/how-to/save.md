---
title: " Rich text editor how to section"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to update the value using shortcut keys."
---

# Capture ctrl+s to update the value

To achieve this, we need to bind the `keydown` event to the Rich Text Editor content and capture the `ctrl + s` key press using its keyCode.
In the `keydown` event handler, the `updateValue` method is called to update the [`value`](../../api/rich-text-editor/#value) property and then we can save the content in the required database using the same.

{% tab template="rich-text-editor/how-to", es5Template="save" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({});
defaultRTE.appendTo('#defaultRTE');

defaultRTE.contentModule.getDocument().addEventListener("keydown",function(e: any):void{
  if(e.key === 's' && e.ctrlKey===true){
        e.preventDefault(); // to prevent default ctrl+s action
        defaultRTE.updateValue(); // to update the value after editing
        let value: any= defaultRTE.value; // you can get the RTE content to save in the desired database
  }
});


```

{% endtab %}