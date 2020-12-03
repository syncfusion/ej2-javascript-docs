---
title: "Rich text editor Validation"
component: "Rich Text Editor"
description: "This section shows how to validate the Syncfusion JavaScript Rich Text Editor control's value by applying validationRules and validationMessage."
---

# Validation

## Validation rules

The Rich Text Editor provides the functionality of character count and its validation. So, you can validate the Rich Text Editor's value on form submission by applying validationRules and validationMessage to the Rich Text Editor.

| Rules | Description |
|----------------|---------|
| required | Requires value for the Rich Text Editor control.|
| minlength | Requires the value to be of given minimum characters count.|
| maxlength | Requires the value to be of given maximum characters count.|

This sample is used to validate form using the obtrusive Validation. Type the values in Rich Text Editor and the form enables the validation with the formvalidator rules by clicking on the submit externally. All rules are validated by the formvalidator rules.

{% tab template="rich-text-editor/form-validation", es5Template="validation" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { FormValidator } from '@syncfusion/ej2-inputs';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar);
import { Button } from '@syncfusion/ej2-buttons';

let button: Button;
let defaultRTE: RichTextEditor = new RichTextEditor({ showCharCount: true, maxLength: 100, placeholder: 'Type something',
change : function() {
  button.disabled = false;
}
});
defaultRTE.appendTo('#defaultRTE');
  let dialog: Dialog;
 button = new Button({
disabled :true
     });
button.appendTo('#validateSubmit');

new FormValidator('#form-element');

```

{% endtab %}

## Validation message

The default error message for a rule can be customizable by defining it along with the concern rule object as follows.

In the following sample, customize the error message along with the concern rule.

{% tab template="rich-text-editor/form-sample", es5Template="validation" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar);
import { Button } from '@syncfusion/ej2-buttons';

let button: Button;
let defaultRTE: RichTextEditor = new RichTextEditor({ showCharCount: true, maxLength: 100, placeholder: 'Type something' ,
change : function() {
   button.disabled = false;
} });
defaultRTE.appendTo('#defaultRTE');

button = new Button({
disabled :true
     });
button.appendTo('#validateSubmit');

let option: FormValidatorModel = {
  rules: {
    // Initialize the CustomPlacement.
    defaultRTE: {
      required: true,
      minLength: [20, 'Need atleast 6 character length'],
      maxLength:[100, 'Maximum 100 character only']
    }
  },
  customPlacement: (inputElement: HTMLElement, dateError: HTMLElement)=>{
    document.getElementById('dateError').appendChild(dateError);
  }
};

let formObject: FormValidator = new FormValidator('#form-element', option);

```

{% endtab %}

## Custom placement of validation message

The FormValidator has an event [customPlacement](../api/form-validator/formValidatorModel/#customplacement) which can be used to place the error message from default position to desired custom location.

{% tab template="rich-text-editor/form-sample", es5Template="custom-placement" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { FormValidator, FormValidatorModel } from '@syncfusion/ej2-inputs';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, Count, QuickToolbar);
import { Button } from '@syncfusion/ej2-buttons';

let button: Button;
let defaultRTE: RichTextEditor = new RichTextEditor({ showCharCount: true, maxLength: 100, placeholder: 'Type something' ,
change : function() {
    button.disabled = false;
} });
defaultRTE.appendTo('#defaultRTE');

button = new Button({
disabled :true
     });
button.appendTo('#validateSubmit');

let option: FormValidatorModel = {
  rules: {
  // Initialize the CustomPlacement.
  defaultRTE: { required:  [true, 'RTE: value is required'], minLength: [15, 'RTE: Need atleast 6 character length'], maxLength:[100, 'RTE: Maximum 100 character only']  }
  },
  customPlacement: (inputElement: HTMLElement, error: HTMLElement)=>{
    document.getElementById('error').appendChild(error);
  }
};
let formObject: FormValidator = new FormValidator('#form-element', option);

```

{% endtab %}
