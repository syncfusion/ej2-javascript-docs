---
title: "Auto Close"
component: "Sidebar"
description: "Sidebar can be initialized in expand or collapsed state in user specified resolutions."
---

# Auto-close

The Sidebar often behaves differently on mobile display and differently on desktop display. It has an effective feature that offers to set it in opened or closed state depending on the specified resolution. This is achieved through [`mediaQuery`](../api/sidebar/#mediaquery) property that allows you to set the Sidebar in an expanded state or collapsed state only in user-defined resolution.

In the following sample, mediaQuery has been used to close and open the Sidebar based on a specific resolution.

{% tab template="sidebar/web", es5Template="es5_sidebar_template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

let defaultSidebar: Sidebar = new Sidebar({
    mediaQuery: window.matchMedia('(min-width: 600px)'), width: "280px",
});
defaultSidebar.appendTo('#default');
    //end of Sidebar initialization
}

```

{% endtab %}

* In the following sample,the Sidebar will be in an expanded state only in resolution below `400px`.

{% tab template="sidebar/mobile", es5Template="sidebar_autoclose_template", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
    //start of sidebar initialization
let defaultSidebar: Sidebar = new Sidebar({
    mediaQuery: window.matchMedia('(max-width: 400px)'), width: "280px",
});
defaultSidebar.appendTo('#default');
    //end of sidebar initialization
}

```

{% endtab %}