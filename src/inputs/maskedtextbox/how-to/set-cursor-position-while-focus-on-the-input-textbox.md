# Set cursor position while focus on the input textbox

By default, on focusing the MaskedTextBox the entire mask gets selected. You can customize by using any one of the following methods:

* Setting cursor position at the start of the MaskedTextBox.
* Setting cursor position at the end of the MaskedTextBox.
* Setting cursor at the specified position in the MaskedTextBox.

> The **selectionStart** and **selectionEnd** set to **0** instead of the input element value's length, when we focus on a MaskedTextBox control filled with all mask characters. This is the default behavior of the HTML 5 input element.

Following is an example that demonstrates the above cases to set cursor position in the MaskedTextBox using [`focus`](../../api/maskedtextbox#focus) event.

{% tab template="maskedtextbox/cursor-position", sourceFiles="app.ts,index.html,styles.css", es5Template="cursor-template" %}

```typescript

import { MaskedTextBox } from '@syncfusion/ej2-inputs';

// initializes the First MaskedTextBox component
let mask: MaskedTextBox = new MaskedTextBox({
  // Default MaskedTextBox
  mask: '00000-00000',
  value: '93828-3213',
  placeholder: 'Default cursor position',
  floatLabelType: 'Always'
});

mask.appendTo('#mask1');

// initializes the Second MaskedTextBox component
let mask1: MaskedTextBox = new MaskedTextBox({
  // sets mask format to the MaskedTextBox
  mask: '00000-00000',
  value: '83929-4343',
  placeholder: 'Cursor positioned at start',
  floatLabelType: 'Always',
  focus: function(args) {
    //sets cursor position at start of MaskedTextBox
    args.selectionEnd = args.selectionStart = 0;
  }
});

mask1.appendTo('#mask2');

// initializes the Third MaskedTextBox component
let mask2: MaskedTextBox = new MaskedTextBox({
  // sets mask format to the MaskedTextBox
  mask: '00000-00000',
  value: '83929-3213',
  placeholder: 'Cursor positioned at end',
  floatLabelType: 'Always',
  focus: function(args) {
    //sets cursor position at end of MaskedTextBox
    args.selectionStart = args.selectionEnd = args.maskedValue.length;
  }
});

mask2.appendTo('#mask3');

// initializes the Fourth MaskedTextBox component
let mask3: MaskedTextBox = new MaskedTextBox({
  // sets mask format to the MaskedTextBox
  mask: '+1 000-000-0000',
  value: '234-432-432',
  placeholder: 'Cursor at specified position',
  floatLabelType: 'Always',
  focus: function(args) {
    //sets cursor at specified position
    args.selectionStart = 3;
    args.selectionEnd = 3;
  }
});

mask3.appendTo('#mask4');

 ```

{% endtab %}