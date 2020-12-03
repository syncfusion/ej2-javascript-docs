# Show tooltip on disabled elements and disable tooltip

By default, tooltips will not be displayed on disabled elements. However, you can enable this behavior by using the following steps:

1. Add a disabled element like the `button` element into a div whose display style is set to `inline-block`.
2. Set the pointer event as `none` for the disabled element (button) through CSS.
3. Initialize the tooltip for outer div element that holds the disabled button element.

{% tab template="tooltip/disabled-elements", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="disabled-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button, Switch } from '@syncfusion/ej2-buttons';

let tooltipObj_1: Tooltip = new Tooltip({
  content: 'Tooltip from disabled element'
});
tooltipObj_1.appendTo('#box');


//Initialize Button component
let buttonObj_1: Button = new Button({
  disabled: true
});
//Render initialized Button component
buttonObj_1.appendTo('#disabledbutton');

//Initialize Button component
let button: Button = new Button();
//Render initialized Button component
button.appendTo('#tooltip');

//Initialize Tooltip component
let tooltipObj_2: Tooltip = new Tooltip({
  //Set tooltip content
  content: 'Lets go green & Save Earth !!!'
});
//Render initialized Tooltip component
tooltipObj_2.appendTo('#tooltip');

let switchObj: Switch = new Switch({
  value: 'USB tethering',
  checked: true,
  change: (args) => {
    if ((document.getElementById('checked') as HTMLInputElement).checked) {
      tooltipObj_2.appendTo('#tooltip');
    } else {
      tooltipObj_2.destroy();
    }
  }
});
switchObj.appendTo('#checked');
```

{% endtab %}
