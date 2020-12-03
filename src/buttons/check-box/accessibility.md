---
title: "CheckBox Accessibility"
component: "CheckBox"
description: "TypeScript CheckBox component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

The web accessibility makes web content and web applications more accessible for people with disabilities. It especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies.
CheckBox provides built-in compliance with `WAI-ARIA` specifications. `WAI-ARIA` support is achieved through the attributes like `aria-checked` and `aria-disabled`. It helps the people with disabilities by providing information about the widget for assistive
technology in the screen readers. CheckBox component contains the `checkbox` role.

| Properties | Functionality |
| ------------ | ----------------------- |
| role | Indicates the type of input element. |
| aria-checked | Indicates whether the input is checked, unchecked, or represents mixture of checked and unchecked values. |
| aria-disabled | Indicates that the element is perceivable but disabled, so it is not editable or otherwise operable. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Space</kbd></td><td>
When the checkbox has focus, pressing the Space key changes the state of the checkbox.</td></tr>
</table>

{% tab template= "check-box/state", sourceFiles="app.ts,index.html,styles.css",
es5Template="state-template", isDefaultActive=true %}

```typescript
import { CheckBox } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//checked state.
let checkbox: CheckBox = new CheckBox({ label: 'Checked State', checked: true });
checkbox.appendTo('#checkbox1');

//unchecked state.
checkbox = new CheckBox({ label: 'Unchecked State' });
checkbox.appendTo('#checkbox2');

//indeterminate state.
checkbox = new CheckBox({ label: 'Indeterminate State', indeterminate: true });
checkbox.appendTo('#checkbox3');

```

{% endtab %}