# Dynamic Tooltip content with dynamic HTML

The Tooltip component loads HTML tags using the [content](../content/) template.

The HTML tags such as `<div>`, `<span>`, `bold`, `italic`, `underline`, etc., can be used. Style attributes can also be applied with HTML tags.

Here, Bold, Italic, Underline, and Anchor tags are used.

When using HTML elements as content to `Tooltip` make the content element `display: none`, then from the
[`beforeRender`](../../api/tooltip#beforerender)
event we can make the element visible again using below code.

```typescript
    document.getElementById('content').style.display = 'block';
```

{% tab template="tooltip/html-content", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="html-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';

//Define an array of JSON data
let title: Tooltip = new Tooltip({
    cssClass: 'e-tooltip-css',
    position: 'BottomCenter',
    opensOn: 'Hover',
    beforeRender: onBeforeRender,
    content: document.getElementById('tooltip')
});
title.appendTo('#Title');

let btn: Button = new Button();
btn.appendTo('#Title');

function onBeforeRender() {
    if(document.getElementById('tooltip')) {
        document.getElementById('tooltip').style.display = 'block';
    }
}
```

{% endtab %}