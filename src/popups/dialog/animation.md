---
title: "Animation"
component: "Dialog"
description: "Explains how to open or close the modal dialog control with various animation effects, duration, and delay (animation dialog box)."
---

# Animation

The Dialog can be animated during the open and close actions. Also, user can
customize animation's [`delay`](../api/dialog/animationSettings/#delay),
[`duration`](../api/dialog/animationSettings/#duration)
and [`effect`](../api/dialog/animationSettings/#effect) by using [animationSettings](../api/dialog/#animationsettings) property.

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
delay</td><td>
The Dialog animation will start with the mentioned delay</td></tr>
<tr>
<td>
duration</td><td>
Specifies the animation duration to complete with one animation cycle</td></tr>
<tr>
<td>
effect</td><td>
Specifies the animation effects of Dialog open and close actions effect.
<br /><br />
List of supported animation effects:
<br />
'Fade' | 'FadeZoom' | 'FlipLeftDown' | 'FlipLeftUp' | 'FlipRightDown' | 'FlipRightUp' | 'FlipXDown' |
'FlipXUp' | 'FlipYLeft' | 'FlipYRight' | 'SlideBottom' | 'SlideLeft' | 'SlideRight' | 'SlideTop' |
'Zoom'| 'None'
<br /><br />
If the user sets ‘Fade’ effect, then the Dialog will open with ‘FadeIn’ effect and close with ‘FadeOut’ effect
</td></tr>
</table>

In the below sample, `Zoom` effect is enabled. So, The Dialog will open with `ZoomIn`
and close with `ZoomOut` effects.

{% tab template="dialog/animation",sourceFiles="app.ts,index.html,styles.css", es5Template="animation-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Dialog component
let dialog = new Dialog({
    //Animation options
    animationSettings: {
        effect: 'Zoom',
        duration: 400,
        delay: 0
    },
    // Enables the header
    header: 'Dialog',
    // Dialog content
    content: 'Dialog enabled with Zoom effect',
    // Enables the footer buttons
    buttons: [
        {
            // Click the footer buttons to hide the Dialog
            'click': () => { dialog.hide(); },
            // Accessing button component properties by buttonModel property
            buttonModel: {
                content: 'OK',
                isPrimary: true
            }
        },
        {
            'click': () => { dialog.hide(); },
            buttonModel: {
                content: 'Cancel',
                cssClass: 'e-flat'
            }
        }
    ],
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '250px'
});
// Render initialized Dialog
dialog.appendTo('#dialog');
// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
    dialog.show();
}

```

{% endtab %}
