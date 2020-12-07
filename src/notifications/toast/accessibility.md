---
title: "Accessibility"
component: "Toast"
description: "The Toast component has accessibility support to access the features via keyboard, screen readers, or other assistive technology devices."
---

# Accessibility

The toast component has been designed with [WAI-ARIA](http://www.w3.org/WAI/PF/aria-practices/) specifications in mind by applying the prompt WAI-ARIA roles, states, and properties with the keyboard support. It helps users who use assistive WAI-ARIA accessibility support, which is achieved using attributes.

It provides information about the elements in a document for assistive technology.

The toast component implements the keyboard navigation support by using the following [WAI-ARIA practices](https://www.w3.org/TR/wai-aria-practices/) and is tested in major screen readers.

## ARIA attributes

<!-- markdownlint-disable MD033 -->

| Class | Description |
| -------- | -------- |
| role |  <b>alert:</b> Identifies the element as a container when alert content will be added or updated. |

{% tab template="toast/toast", es5Template="es5_toast", sourceFiles="index.ts,index.html"  %}

```typescript
import {Toast} from '@syncfusion/ej2-notifications';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let toast: Toast = new Toast({
    title: 'Matt sent you a friend request',
    content: 'You have a new friend request yet to accept',
    timeOut: 0
});
toast.appendTo('#element');
toast.show();
```

{% endtab %}