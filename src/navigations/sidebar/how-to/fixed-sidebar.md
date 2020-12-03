---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Sidebar with fixed position

The following example demonstrates how to render sidebar with fixed position. When scroll the main content area, the position of the sidebar will not change.

{% tab template="sidebar/fixed-position", es5Template="es5_sidebar_fixed_position", isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

// Sidebar Initialization
let defaultSidebar: Sidebar = new Sidebar({
    width:'260px',
   created: onCreate
  });
  defaultSidebar.appendTo('#default-sidebar');
  //end of Sidebar initialization  

document.getElementById('hamburger').onclick = (): void => {
  defaultSidebar.toggle();
}
function onCreate(): void {
    this.element.style.visibility = '';
}

```

{% endtab %}
