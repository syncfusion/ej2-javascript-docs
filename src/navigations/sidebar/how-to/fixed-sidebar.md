---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Sidebar with fixed position

The Sidebar does not require any specific style to make it as a fixed one. By default, the Sidebar position will be in fixed state. The following example demonstrates that the Sidebar is rendered with a fixed position. The position of the Sidebar will not change when scrolling the main content area.

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
