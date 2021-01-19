---
title: "Add Font Awesome icons"
component: "Toolbar"
description: "This example demonstrates how to add the font awesome icons into Essential JS Toolbar items."
---

# Add Font Awesome

We can customize the Toolbar component items by using font awesome icons and fonts.

* Need to add font awesome CDN reference link in your sample to use font awesome icons.

```html

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" />

```

You can add the font awesome icons to the toolbar component using ['prefixIcon'](../../api/toolbar/itemDirective/#prefixicon) property. The following sample illustrates how to use font awesome in toolbar component.

{% tab template="toolbar/add-font-awesome", es5Template="es5_font_awesome", sourceFiles="index.ts,index.html,index.css" %}

```typescript

import { Toolbar } from "@syncfusion/ej2-navigations";
let toolbar: Toolbar = new Toolbar({
  items: [
    { prefixIcon: "fa fa-twitter" },
    { prefixIcon: "fa fa-facebook" },
    { prefixIcon: "fa fa-whatsapp" },
    { template: '<button class="e-btn e-tbar-btn"><span style="font-size: 3em; color: Tomato;"><i class="e-icons fa fa-twitter"></i</span></button>' }
  ]
});
toolbar.appendTo("#element");

```

{% endtab %}

> We can also use templates for rendering icons based on customized requirement.

## Customization

The class “e-icons” is used for standardizing the icons appearance to fit into toolbar items. If you rather wish to override the appearance of the icons used, you could do this by using the below set of classes

Use the following CSS to set the color of icons.

```CSS

    .e-toolbar .e-icons {
        color: #e3165b !important;
    }

```

Use the following CSS to set the font size of icons.

```CSS

    .e-toolbar .e-btn .e-icons.e-btn-icon {
        font-size: 14px !important;
    }

```