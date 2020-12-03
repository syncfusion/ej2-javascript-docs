# Show Slider from Hidden state

This section demonstrates how-to render the Slider component in hidden state and make it visible in button click. We can initialize Slider in hidden state by setting the display as none.

In the sample, by clicking on the button, we can make the Slider visible from hidden state, and we must also call the [`refresh`](../api/base/component/#refresh) method of the Slider to render it properly based on its original dimensions.

{% tab template="slider/hidden-slider", isDefaultActive = "true", sourceFiles="app.ts,index.html,index.css", es5Template="hidden-slider" %}

```typescript

import { Slider, SliderChangeEventArgs } from '@syncfusion/ej2-inputs';
import { Button } from '@syncfusion/ej2-buttons';

// Initialize the Button component.
let button: Button = new Button({ content: 'Button' });
// Render initialized button.
button.appendTo('#element');

// Initialize Slider Component
let defaultObj: Slider = new Slider({
    // Set slider minimum and maximum values
    // new Date(Year, Month, day, hours, minutes, seconds, millseconds)
    min: new Date(2013, 6, 13, 11).getTime(), max: new Date(2013, 6, 13, 17).getTime(),
    // 3600000 milliseconds = 1 Hour
    step: 3600000,
    //Set buttons for slider
    showButtons: true,
    // Set the initial range values for slider
    value: new Date(2013, 6, 13, 13).getTime(),
    // Bind Tooltip change event for custom formatting
    tooltipChange: tooltipChangeHandler,
    // Initialize tooltip with placement
    tooltip: {
        placement: 'Before', isVisible: true, cssClass: 'e-tooltip-cutomization'
    },
    // Bind ticks event for custom formatting
    renderingTicks: renderingTicksHandler,
    // Initialize ticks with placement, largestep, smallstep
    ticks: {
        placement: 'After',
        // 2 * 3600000 milliseconds = 2 Hour
        largeStep: 2 * 3600000,
        smallStep: 3600000, showSmallTicks: true
    },
    // Set the type to render range slider
    type: 'MinRange'
});
defaultObj.appendTo('#slider');

function tooltipChangeHandler(args: SliderTooltipEventArgs): void {
    /**
     * toLocaleTimeString is predefined javascript date function, which is used to
     * customize the date in different format
     */
    let custom: { [key: string]: string } = { hour: '2-digit', minute: '2-digit' };
    // Splitting the range values from the tooltip using space into an array.
    if (args.text.indexOf('-') !== -1) {
        let totalMilliSeconds: string[] = args.text.split(' ');
        // First part is the first handle value
        let firstPart: string = totalMilliSeconds[0];
        // Second part is the second handle value
        let secondPart: string = totalMilliSeconds[2];

        firstPart = new Date(Number(firstPart)).toLocaleTimeString('en-us', custom);
        secondPart = new Date(Number(secondPart)).toLocaleTimeString('en-us', custom);
    } else {
        args.text =  new Date(Number(args.text)).toLocaleTimeString('en-us', custom);
    }
}

function renderingTicksHandler(args: SliderTickEventArgs): void {
    let totalMilliSeconds: number = Number(args.value);
    /**
     * toLocaleTimeString is predefined javascript date function, which is used to
     * customize the date in different format
     */
    let custom: { [key: string]: string } = { hour: '2-digit', minute: '2-digit' };
    // Assigning our custom text to the tick value.
    args.text = new Date(totalMilliSeconds).toLocaleTimeString('en-us', custom);
}

//Visible slider by clicking the button
document.getElementById('element').onclick = function () {
    let slider = document.getElementById("case");
    let ticks = document.getElementById("slider");
    slider.style.display = "block";
    ticks.ej2_instances[0].refresh();
};
```

{% endtab %}