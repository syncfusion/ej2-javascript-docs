---
title: "Positions"
component: "Toast"
description: "The Toast component position section explains how to customize the toast position or update the toast predefined position."
---

# Positions

The toast position can be updated based on predefined positions or customizable positions. The predefined position combinations are updated in the [X](../api/toast/toastPositionModel/#x) and [Y](../api/toast/toastPositionModel/#y) position properties.

## Predefined

`X` Positions

* Left
* Center
* Right

`Y` Positions

* Top
* Bottom

> In multiple toast display, the new toast position will not be updated on dynamic change of property values until the old toast messages removed.
> The toast occupies full width when you set the width to '100%', so the X positions will not affect the changes when the width is '100%'.

## Custom

Custom `X` and `Y` positions can be given as pixels/numbers/percentage. The number value is considered as pixels based on the top and left values updated in the toast.

{% tab template="toast/custom_pos", es5Template="es5_toast_position", isDefaultActive=true, sourceFiles="index.ts,index.html"  %}

```typescript
import { Toast } from '@syncfusion/ej2-notifications';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { RadioButton, ChangeEventArgs as CheckBoxChange } from '@syncfusion/ej2-buttons';


let toastObj: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    icon: 'e-laura',
    target: document.body,
    position: { X: 'Right', Y: 'Bottom' }
});

let listObj: DropDownList = new DropDownList({
    index: 5,
    // set the placeholder to DropDownList input element
    placeholder: 'Select a position',
    // set the height of the popup element
    popupHeight: '200px',
    // bind the change event
    change: valueChange
});
listObj.appendTo('#position');
let radioButton: RadioButton = new RadioButton({ label: 'Target', name: 'toast', value: 'Target', change: checkboxChange });
radioButton.appendTo('#radio1');

let radioButton2 = new RadioButton({ label: 'Global', name: 'toast', value: 'Global', checked: true, change: checkboxChange1 });
radioButton2.appendTo('#radio2');

let radioButton1 = new RadioButton({ label: 'Position', name: 'toastPos', value: 'Position', checked: true, change: checkboxChange2 });
radioButton1.appendTo('#dropdownRadio');

let radioButton3 = new RadioButton({ label: 'Custom', name: 'toastPos', value: 'Custom', change: checkboxChange3 });
radioButton3.appendTo('#customRedio');

toastObj.appendTo('#toast_pos');
toastShow(200);

function toastShow(timeOutDelay: number): void {
    setTimeout(
        () => {
            toastObj.show();
        }, timeOutDelay);
}
document.getElementById('show_Toast').onclick = () => {
    if (customFlag) {
        setcustomPosValue();
    }
    toastObj.show();
};

document.getElementById('hideToast').onclick = () => {
    toastObj.hide('All');
};
let customFlag: boolean = false;

function checkboxChange(e: CheckBoxChange): void {
    if (this.checked) {
        toastObj.hide('All');
        toastObj.target = '#toast_pos_target';
        toastShow(1000);
    }
}

function checkboxChange1(e: CheckBoxChange): void {
    if (this.checked) {
        toastObj.hide('All');
        toastObj.target = document.body;
        toastShow(1000);
    }
}

function checkboxChange2(e: CheckBoxChange): void {
    if (this.checked) {
        toastObj.hide('All');
        document.getElementById('dropdownChoose').style.display = 'table-cell';
        document.getElementById('customChoose').style.display = 'none';
        setToastPosValue(listObj.value.toString()); customFlag = false; toastShow(1000);
    }
}

function checkboxChange3(e: CheckBoxChange): void {
    if (this.checked) {
        toastObj.hide('All');
        document.getElementById('dropdownChoose').style.display = 'none';
        document.getElementById('customChoose').style.display = 'table-cell';
        setcustomPosValue(); customFlag = true; toastShow(1000);
    }
}

//Setting Toast Custom Position
function setcustomPosValue(): void {
    toastObj.position.X = parseInt((<HTMLInputElement>document.getElementById('xPos')).value, 10);
    toastObj.position.Y = parseInt((<HTMLInputElement>document.getElementById('yPos')).value, 10);
}

//Setting Toast Position
function setToastPosValue(value: string): void {
    switch (value) {
        case 'topleft':
            toastObj.position.X = 'Left'; toastObj.position.Y = 'Top'; break;
        case 'topright':
            toastObj.position.X = 'Right'; toastObj.position.Y = 'Top'; break;
        case 'topcenter':
            toastObj.position.X = 'Center'; toastObj.position.Y = 'Top'; break;
        case 'topfullwidth':
            toastObj.width = '100%'; toastObj.position.X = 'Center'; toastObj.position.Y = 'Top'; break;
        case 'bottomleft':
            toastObj.position.X = 'Left'; toastObj.position.Y = 'Bottom'; break;
        case 'bottomright':
            toastObj.position.X = 'Right'; toastObj.position.Y = 'Bottom'; break;
        case 'bottomcenter':
            toastObj.position.X = 'Center'; toastObj.position.Y = 'Bottom'; break;
        case 'bottomfullwidth':
            toastObj.width = '100%'; toastObj.position.X = 'Center'; toastObj.position.Y = 'Bottom'; break;
    }
}

function valueChange(e: ChangeEventArgs): void {
    toastObj.hide('All'); setToastPosValue(e.value.toString()); toastShow(1000);
}

```

{% endtab %}

## See Also

* [Render toast with different positions](./how-to/show-multiple-toasts-in-various-positions/)