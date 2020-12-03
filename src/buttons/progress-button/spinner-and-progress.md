---
title: "ProgressButton Spinner and Progress"
component: "ProgressButton"
description: "TypeScript ProgressButton allows the user to change size & position of the spinner, customize spinner using template and to change the progress."
---

<!-- markdownlint-disable MD002 MD022 -->
## Spinner

### Change spinner position

Spinner position can be changed by modifying the [`position`](../api/progress-button/spinSettingsModel#position) property of [`spinSettingsModel`](../api/progress-button/spinSettingsModel). By default, the spinner is positioned at the left of the ProgressButton. You can position it at the `left`, `right`, `top`, `bottom`, or `center` of the text content.

### Change spinner size

Spinner size can be changed by modifying the [`width`](../api/progress-button/spinSettingsModel#width) property of [`spinSettingsModel`](../api/progress-button/spinSettingsModel). In this demo, the `width` is set to `20` to change the spinner size.

### Spinner template

You can use custom spinner by specifying the [`template`](../api/progress-button/spinSettingsModel#template) property of [`spinSettingsModel`](../api/progress-button/spinSettingsModel) with custom styles.

The following sample demonstrates the above functionalities of the spinner.

{% tab template="progress-button/spinner", sourceFiles="app.ts,index.html,styles.css", es5Template="spinner" %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({ content: 'Submit', spinSettings: { position: 'Right', width: 20, template: '<div class="template"></div>' } });

progressBtn.appendTo('#progressbtn');
```

{% endtab %}

## Progress

### Content animation

The [`content`](../api/progress-button#content) of the ProgressButton can be animated during progress using the [`effect`](../api/progress-button/animationSettingsModel#effect) property of [`animationSettingsModel`](../api/progress-button/animationSettingsModel). You can also set custom duration and timing function using the [`duration`](../api/progress-button/animationSettingsModel#duration) and [`easing`](../api/progress-button/animationSettingsModel#easing) properties. The possible `effect` values are `None`, `SlideLeft`, `SlideRight`, `SlideUp`, `SlideDown`, `ZoomIn`, and `ZoomOut`.

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html", es5Template="animation" %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({ content: 'Slide Left', enableProgress: true, animationSettings: { effect: 'SlideLeft', duration: 500, easing: 'linear' }, spinSettings: { position: 'Center' } });

progressBtn.appendTo('#progressbtn');
```

{% endtab %}

### Change step of the ProgressButton

The progress can be visualized at the specified interval by changing the [`step`](../api/progress-button/progressEventArgs#step) property in the [`begin`](../api/progress-button#begin) event of the ProgressButton. In this demo, the `step` property is set to `20` to show progress at every 20% increment.

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html", es5Template="step" %}

```typescript
import { ProgressButton, ProgressEventArgs } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({
    content: 'Progress Step', enableProgress: true,
    begin: (args: ProgressEventArgs) => {
        args.step = 20;
    }, cssClass: 'e-hide-spinner'
});

progressBtn.appendTo('#progressbtn');
```

{% endtab %}

> The class `e-hide-spinner` hides the spinner in the ProgressButton, For more information, see [hide spinner](./how-to/hide-spinner) section.

### Change progress dynamically

The progress can be changed dynamically by modifying the [`percent`](../api/progress-button/progressEventArgs#percent) property in the ProgressButton events. In this demo, on 40% completion of progress, the `percent` property is set to `90` to show dynamic change of the progress.

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html", es5Template="percent" %}

```typescript
import { ProgressButton, ProgressEventArgs } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({
    content: 'Progress', enableProgress: true, duration: 15000,
    begin: (args: ProgressEventArgs) => {
        progressBtn.content = 'Progress ' + args.percent + '%';
        progressBtn.dataBind();
    },
    progress: (args: ProgressEventArgs) => {
        progressBtn.content = 'Progress ' + args.percent + '%';
        progressBtn.dataBind();
        if (args.percent === 40) {
            args.percent = 90
        }
    },
    end: (args: ProgressEventArgs) => {
        progressBtn.content = 'Progress ' + args.percent + '%';
        progressBtn.dataBind();
    },
    cssClass: 'e-hide-spinner'
});

progressBtn.appendTo('#progressbtn');
```

{% endtab %}

> The method [`dataBind`](../api/progress-button#databind) applies the property changes immediately to the component.

### Start and stop methods

You can pause and resume the progress using the [`stop`](../api/progress-button#start) and [`start`](../api/progress-button#stop) methods, respectively. In this demo, clicking the ProgressButton will pause and resume the progress.

{% tab template="progress-button/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="methods" %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({
    content: 'Download', enableProgress: true, duration: 4000, iconCss: 'e-btn-sb-icon e-download',
    end: () => {
        progressBtn.content = 'Download';
        progressBtn.iconCss = 'e-btn-sb-icon e-download';
        progressBtn.dataBind();
    },
    cssClass: 'e-hide-spinner'
});
progressBtn.appendTo('#progressbtn');

progressBtn.element.addEventListener('click', clickHandler);

function clickHandler(): void {
    if (progressBtn.content === 'Download') {
        progressBtn.content = 'Pause';
        progressBtn.iconCss = 'e-btn-sb-icon e-pause';
        progressBtn.dataBind();
    }
    // clicking on ProgressButton will stop the progress when the text content is 'Pause'
    else if (progressBtn.content === 'Pause') {
        progressBtn.content = 'Resume';
        progressBtn.iconCss = 'e-btn-sb-icon e-play';
        progressBtn.dataBind();
        progressBtn.stop();
    }
    // clicking on ProgressButton will start the progress when the text content is 'Resume'
    else if (progressBtn.content === 'Resume') {
        progressBtn.content = 'Pause';
        progressBtn.iconCss = 'e-btn-sb-icon e-pause';
        progressBtn.dataBind();
        progressBtn.start();
    }
}
```

{% endtab %}

## See Also

* [How to hide spinner](./how-to/hide-spinner)
* [Customize ProgressButton using cssClass](how-to/customize-progress-using-cssclass)