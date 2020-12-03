---
title: "Tooltip Content"
component: "Tooltip"
description: "TypeScript tooltip component's content can be assigned with static text, template, or loaded dynamically via AJAX."
---

# Content

A text or a piece of information assigned to the Tooltip's `content` property will be displayed as the main text stream of the Tooltip.
 It can be a string or a template content. If the `content` property is not provided with any specific value, then it takes the value
  assigned to the `title` attribute of the target element on which the Tooltip was initialized. The content can also dynamically be
   assigned to the Tooltip via AJAX.

## Template content

Any text or image can be added to the Tooltip, by default. To customize the Tooltip layout or to create your own visualized element on the
 Tooltip, template can be used.

Refer to the following code example to add formatted HTML content to the Tooltip.

{% tab template="tooltip/content", isDefaultActive=true, sourceFiles="index.ts,index.html",es5Template="content-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';

let tooltipContent: HTMLElement = document.createElement("div");
tooltipContent.innerHTML = "<p><strong>Environmentally friendly</strong> or <strong>environment-friendly</strong>, <i>(also referred to as eco-friendly, nature-friendly, and green)</i> are marketing and sustainability terms referring to goods and services, laws, guidelines and policies that inflict reduced, minimal, or no harm upon ecosystems or the environment.</p>";
let tooltip: Tooltip = new Tooltip({
    content: tooltipContent
});
tooltip.appendTo('#target');

```

{% endtab %}

## Dynamic content via AJAX

The Tooltip content can be dynamically loaded  by making use of the AJAX call. The AJAX request is usually made within the `beforeRender`
 event of the Tooltip, and then the Tooltip's `content` is assigned the value retrieved on it's success.

{% tab template="tooltip/ajax-content", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css",es5Template="ajax-content-template" %}

```typescript
import { Tooltip, TooltipEventArgs } from '@syncfusion/ej2-popups';
import { Ajax } from '@syncfusion/ej2-base';

let tooltip: Tooltip = new Tooltip({
        content: 'Loading...',
        target: '.target',
        position: 'RightCenter',
        beforeRender: onBeforeRender
});
tooltip.appendTo('#targetContainer');

function onBeforeRender(args: TooltipEventArgs): void {
    let ajax: Ajax = new Ajax('./tooltipdata.json', 'GET', true);
    ajax.send().then(
        (result: any) => {
            result = JSON.parse(result);
            for (let i: number = 0; i < result.length; i++) {
                if (result[i].Id === args.target.getAttribute('data-content')) {
                    this.content = "<div class='contentWrap'><div>" + result[i].Sports + "</div></div>";
                }
            }
            this.dataBind();
        },
        (reason: any) => {
            this.content = reason;
            this.dataBind();
        });
}

```

{% endtab %}
