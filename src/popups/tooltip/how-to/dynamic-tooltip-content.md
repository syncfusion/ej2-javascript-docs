# Dynamic Tooltip Content

The tooltip content can be changed dynamically using the [AJAX](../../api/base/ajax/) request.

The AJAX request should be made within the [`beforeRender`](../../api/tooltip#beforerender) event of the tooltip. On every success, the corresponding retrieved data will be set to the [content](../../api/tooltip#content) property of the tooltip.

When you hover over the icons, its respective data will be retrieved dynamically and then assigned to the tooltip’s content.

Refer to the following code snippet to change the tooltip content dynamically.

```typescript
function onBeforeRender(args: TooltipEventArgs): void {
    this.content = 'Loading...';
    this.dataBind();
    let ajax: Ajax = new Ajax('./tooltip.json', 'GET', true);
    ajax.send().then(
        (result: any) => {
            result = JSON.parse(result);
            for (let i: number = 0; i < result.length; i++) {
                if (result[i].Id == args.target.id) {
                    /* tslint:disable */
                    this.content = result[i].Sports;
                    /* tslint:enable */
                }
            }
            this.dataBind();
        },
        (reason: any) => {
            this.content = reason.message;
            this.dataBind();
        });
}
```

{% tab template="tooltip/dynamic-content", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="dynamic-template" %}

```typescript
import { Tooltip, TooltipEventArgs } from '@syncfusion/ej2-popups';
import { Ajax } from '@syncfusion/ej2-base';

let tooltip: Tooltip = new Tooltip({
    content: 'Loading...',
    target: '.circletool',
    showTipPointer: false,
    beforeRender: onBeforeRender
});

tooltip.appendTo('#box');
function onBeforeRender(args: TooltipEventArgs): void {
    this.content = 'Loading...';
    this.dataBind();
    let ajax: Ajax = new Ajax('./tooltip.json', 'GET', true);
    ajax.send().then(
        (result: any) => {
            result = JSON.parse(result);
            for (let i: number = 0; i < result.length; i++) {
                if (result[i].Id == args.target.id) {
                    /* tslint:disable */
                    this.content = result[i].Name;
                    /* tslint:enable */
                }
            }
            this.dataBind();
        },
        (reason: any) => {
            this.content = reason.message;
            this.dataBind();
        });
}

```

{% endtab %}