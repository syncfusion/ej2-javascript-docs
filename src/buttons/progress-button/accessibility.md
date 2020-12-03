---
title: "ProgressButton Accessibility"
component: "ProgressButton"
description: "TypeScript ProgressButton component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

## ARIA attributes

The web accessibility makes web content and web applications more accessible for people with disabilities. Mostly, it helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies. The ProgressButton provides a built-in compliance with `WAI-ARIA` specifications. The `WAI-ARIA` support is achieved using the `aria-label`, `aria-valuemin`, `aria-valuemax`, and `aria-valuenow` attributes in the ProgressButton. It helps by providing information about the widget for assistive technology in the screen readers.

| Properties | Functionality |
| ------------ | ----------------------- |
| aria-label | Indicates the text content of the ProgressButton. |
| aria-valuemin | Indicates the minimum value for the ProgressButton. |
| aria-valuemax | Indicates the maximum value for the ProgressButton. |
| aria-valuenow | Indicates the current value for the ProgressButton. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Enter/Space</kbd></td><td>
Starts the progress.</td></tr>
</table>

{% tab template= "progress-button/getting-started", sourceFiles="app.ts,index.html",
es5Template="accessibility", isDefaultActive=true %}

```typescript
import { ProgressButton } from '@syncfusion/ej2-splitbuttons';

let progressBtn: ProgressButton = new ProgressButton({content: 'Spin Left', enableProgress: true});

progressBtn.appendTo('#progressbtn');

```

{% endtab %}