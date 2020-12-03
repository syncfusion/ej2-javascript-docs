---
title: "Trace events of ProgressButton"
component: "ProgressButton"
description: "TypeScript ProgressButton how to section, change text content and styles, hide spinner, customize progress, event trace."
---

# Trace events of ProgressButton

The ProgressButton component triggers events based on its actions. The events can be used as extension points to perform custom operations.

The events available in ProgressButton are [`fail`](../../api/progress-button#fail), [`begin`](../../api/progress-button#begin), [`progress`](../../api/progress-button#progress), and [`end`](../../api/progress-button#end).
{% tab template="progress-button/events", sourceFiles="app.ts,index.html,styles.css", es5Template="progress-btn-event" %}

```typescript

import { Button } from '@syncfusion/ej2-buttons';
import { ProgressButton, ProgressEventArgs } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({
    content: 'Progress',
    enableProgress: true,
    begin: (args: ProgressEventArgs) => {
        updateEventLog(args);
    },
    end: (args: ProgressEventArgs) => {
        updateEventLog(args);
    },
    progress: (args: ProgressEventArgs) => {
        updateEventLog(args);
    },
    fail: (args: Event) => {
        updateEventLog(args);
    }
    }, '#progressbtn');

let clear: Button = new Button({ cssClass: 'e-small'});
clear.appendTo('#clear');

clear.element.onclick = () => {
    let propertyElem: HTMLElement = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].innerHTML = '';
}

function updateEventLog(args: any): void {
    let propertyElem: HTMLElement = document.getElementById('propertyTable');
    propertyElem.getElementsByTagName('td')[0].insertAdjacentHTML('beforeend', args.name + ' Event triggered. <br />');
}
```

{% endtab %}
