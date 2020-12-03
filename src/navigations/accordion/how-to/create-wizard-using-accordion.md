---
title: "Create wizard using Accordion"
component: "Accordion"
description: "This online shopping example demonstrates how to create multiple components inside the Essential JS 2 Accordion component."
---

# Create wizard using Accordion

Accordion items can be disabled dynamically by passing the index and boolean value with the [`enableItem`](../../api/accordion#enableitem) method and also dynamically expand the item using [`expandItem`](../../api/accordion#expanditem) method.

The below Wizard sample is designed for Online Shopping model. In this, each Accordion item is integrated with required components to fill
the details and designed for getting user details and making payment at the end. Each field is provided with validation for all mandatory
option to enable/disable to next Accordion.  In below sample, accordion items can be disabled dynamically with [`enableItem`](../../api/accordion#enableitem) method using [`created`](../../api/accordion#created) event.

{% tab template="accordion/accordion-disable-item", es5Template="es5_disable_item", sourceFiles="index.ts,index.html" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';
import { DatePicker } from '@syncfusion/ej2-calendars';
import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { Accordion, ExpandEventArgs } from '@syncfusion/ej2-navigations';

enableRipple(true);

let success: string = 'Your payment successfully processed';
let email_alert: string = 'Enter valid email address';
let mobile_alert: string = 'Mobile number length should be 10';
let card_alert: string = 'Card number length should be 16';
let cvv_alert: string = 'CVV number length should be 3';

let datePicker: DatePicker = new DatePicker({
  width: '100%',
  format: 'MM/yyyy',
  floatLabelType: 'Auto',
  placeholder: 'Expiry Date'
});
datePicker.appendTo("#expiry");

let cardNum: NumericTextBox = new NumericTextBox({
  placeholder: 'Card No',
  floatLabelType: 'Auto',
  format: '0',
  showSpinButton: false
});
cardNum.appendTo('#cardNo');

let cvv: NumericTextBox = new NumericTextBox({
  placeholder: 'CVV',
  floatLabelType: 'Auto',
  format: '0',
  showSpinButton: false
});
cvv.appendTo('#CVV');

let mobile: NumericTextBox = new NumericTextBox({
  placeholder: 'Mobile',
  floatLabelType: 'Auto',
  format: '0',
  showSpinButton: false
});
mobile.appendTo('#mobile');

let alertDialog: Dialog = new Dialog({
  header: 'Alert',
  width: 200,
  isModal: true,
  content: '',
  target: document.body,
  buttons: [{
    buttonModel: { content: 'Ok', isPrimary: true },
    click: (() => {
      alertDialog.hide();
      if (acrdnObj.expandedItems[0] === 2 && alertDialog.content === success) {
        acrdnObj.enableItem(0, true);
        acrdnObj.enableItem(1, false);
        acrdnObj.enableItem(2, false);
        acrdnObj.expandItem(true, 0);
      }
    })
  }]
});
alertDialog.appendTo('#alertDialog');
alertDialog.hide();

let acrdnObj: Accordion = new Accordion({
  expanding: expand,
  created: () => {
   acrdnObj.enableItem(1, false);
   acrdnObj.enableItem(2, false);
  },
  items: [
    { header: 'Sign In', content: '#Sign_In_Form', expanded: true },
    { header: 'Delivery Address', content: '#Address_Fill' },
    { header: 'Card Details', content: '#Card_Fill' },
  ]
});
acrdnObj.appendTo('#element');

function checkMail(mail: string): void {
  if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(mail)) {
    return (true);
  } else {
    alertDialog.content = email_alert;
    alertDialog.show();
    return (false)
  }
}

function checkMobile(mobile: number): void {
  if (mobile.match(/^\d{10}$/)) {
    return (true);
  } else {
    alertDialog.content = mobile_alert;
    alertDialog.show();
    return (false)
  }
}

function checkCardNo(cardNo: number): void {
  if (cardNo.match(/^\d{16}$/)) {
    return (true);
  } else {
    alertDialog.content = card_alert;
    alertDialog.show();
    return (false)
  }
}

function checkCVV(cvv: number): void {
  if (cvv.match(/^\d{3}$/)) {
    return (true);
  } else {
    alertDialog.content = cvv_alert;
    alertDialog.show();
    return (false)
  }
}

function expand(e: ExpandEventArgs): void {
  if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 0) {
    document.getElementById('Continue_Btn').onclick = (e : Event) => {
      let email: string = document.getElementById('email');
      let password: string = document.getElementById('password');
      if(email.value !== '' && password.value !== '') {
        if(checkMail(email.value)) {
          email.value = password.value = '';
          acrdnObj.enableItem(1, true);
          acrdnObj.enableItem(0, false);
          acrdnObj.expandItem(true, 1);
        }
        document.getElementById('err1').classList.remove('show');
      } else {
        document.getElementById('err1').classList.add('show');
      }
    }
  } else if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 1) {
    document.getElementById('Continue_BtnAdr').onclick = (e : Event) => {
      let name: string = document.getElementById('name');
      let address: string = document.getElementById('address');
      let mobile: number = document.getElementById('mobile');
      if((name.value !== '') && (address.value !== '') && (mobile.value !== '')) {
        if(checkMobile(mobile.value)) {
          acrdnObj.enableItem(2, true);
          acrdnObj.enableItem(1, false);
          acrdnObj.expandItem(true, 2);
        }
        document.getElementById('err2').classList.remove('show');
      } else {
        document.getElementById('err2').classList.add('show');
      }
    }
  } else if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 2) {
    document.getElementById('Back_Btn').onclick = (e : Event) => {
      acrdnObj.enableItem(1, true);
      acrdnObj.enableItem(2, false);
      acrdnObj.expandItem(true, 1);
    }
    document.getElementById('Save_Btn').onclick = (e : Event) => {
      let cardHolder: string =document.getElementById('cardHolder');
      let expiry: number = document.getElementById('expiry');
      let cardNo: number = document.getElementById('cardNo');
      let cvv: number = document.getElementById('CVV');
      if((cardNo.value !== '') && (cardHolder.value !== '') && (expiry.value !== '') && (cvv.value !== '')) {
        if (checkCardNo(cardNo.value)) {
          if (checkCVV(cvv.value)) {
            alertDialog.content = success;
            alertDialog.show();
          }
        }
        document.getElementById('err3').classList.remove('show');
      } else {
        document.getElementById('err3').classList.add('show');
      }
    }
  }
}

```

{% endtab %}
