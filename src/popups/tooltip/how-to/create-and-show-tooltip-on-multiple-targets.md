# Create and show tooltip on multiple targets

Tooltip can be created and shown on multiple targets within a container by defining the specific target elements to the target property. So, the tooltip is initialized only on matched targets within a container.

In this case, the tooltip content is assigned from the title attribute of the target element.

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';

let tooltip: Tooltip = new Tooltip({
    position: 'RightCenter'
});
tooltip.appendTo('#uname); // Here we have appended the target to the element.
```

{% tab template="tooltip/form-validation", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="form-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';
import { InputObject } from  '@syncfusion/ej2-inputs';

let button1: Button = new Button();
button1.appendTo('#sample');
let button2: Button = new Button();
button2.appendTo('#clear');
let tooltip1: Tooltip = new Tooltip({
    position: 'RightCenter'
});
tooltip1.appendTo('#uname');
let tooltip2: Tooltip = new Tooltip({
    position: 'RightCenter'
});
tooltip2.appendTo('#mail');
let tooltip3: Tooltip = new Tooltip({
    position: 'RightCenter'
});
tooltip3.appendTo('#pwd');
let tooltip4: Tooltip = new Tooltip({
    position: 'RightCenter'
});
tooltip4.appendTo('#cpwd');
document.getElementById('sample').addEventListener('click', function(){
  let name = document.getElementById('uname').value;
  let pwd = document.getElementById('pwd').value;
  let cpwd = document.getElementById('cpwd').value;
  if(name.length > 0 & name.length < 4){
    document.getElementById('uname').title = 'Required Minimum 4 Characters';
    document.getElementById('uname').style.backgroundColor = 'red';
    let target = document.getElementById('uname');
    tooltip1.open(target);
  } else {

     document.getElementById('uname').style.backgroundColor = 'white';
  }
  if(pwd !== '' && pwd.length < 8){
     document.getElementById('pwd').title = 'Required Minimum 8 Characters';
    document.getElementById('pwd').style.backgroundColor = 'red';
    let pwdtarget = document.getElementById('pwd');
    tooltip3.open(pwdtarget);
  } else {
     document.getElementById('pwd').style.backgroundColor = 'white';
  }
  if(name.length >= 4 && pwd !== '' && pwd.length >= 8  &&  pwd == cpwd ){
     alert('Form Submitted');
  } else {
     alert('Details are not Valid');
  }
})
document.getElementById('clear').addEventListener('click', function(){
  document.getElementById('uname').style.backgroundColor = 'white';
  document.getElementById('pwd').style.backgroundColor = 'white';
  let target = document.getElementById('uname');
  tooltip1.close(target);
  document.getElementById('uname').title = 'Please enter your name';
  let pwdtarget = document.getElementById('pwd');
  tooltip3.close(pwdtarget);
});

```

{% endtab %}