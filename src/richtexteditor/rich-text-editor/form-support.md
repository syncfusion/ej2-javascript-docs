---
title: "Rich text editor Form support"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control demonstrates that how to work with form and it's validation."
---

# Form support

The following sample demonstrates how to get the Rich Text Editor value in button click.

## Render the Rich Text Editor

Render the Rich Text Editor in form.

```typescript

<form id="myForm" class="form-vertical">
<div class="form-group">
<textarea id="defaultRTE" name="defaultRTE" required maxlength="100" minlength="20" data-msg-containerid="dateError">      </textarea>
<div id="dateError" style="padding-top: 10px"></div>
</div>
<div style="text-align: center">
<button id="validateSubmit" class="samplebtn e-control e-btn" type="submit" data-ripple="true">Submit</button>
<button id="resetbtn" class="samplebtn e-control e-btn" type="reset" data-ripple="true">Reset</button>
</div>
</form>

```

## Obtain the value

Upon submitting the form, the `getValue` method will be triggered. Through the `FormData` class, get the Rich Text Editor value.

{% tab template="rich-text-editor/form-sample", es5Template="value" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { FormValidator } from '@syncfusion/ej2-inputs';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({ showCharCount: true, maxLength: 100, placeholder: 'Type something' });
defaultRTE.appendTo('#defaultRTE');

let formObject = new FormValidator('#form-element');

document.getElementById('validateSubmit').onclick = function (){
  getValue();
}

function getValue(){
  let form = document.getElementById('form-element');
  let formData = new FormData(form);
  let rteValue = formData.get('defaultRTE');
  alert(rteValue);//Store the value to the data base.
}

```

{% endtab %}

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to validate the value](./validation/)