---
title: "Add Font Awesome icons"
component: "Accordion"
description: "This example demonstrates how to add the font awesome icons into Essential JS Accordion component."
---

# Add Font Awesome

We can customize the Accordion component items by using font awesome icons.

* Need to add font awesome CDN reference link in your sample to use font awesome icons.

```html

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" />
  
```

You can add the font awesome icons to the Accordion header using ['iconCss'](../../api/accordion/accordionItem#iconcss) property. The following sample illustrates how to use font awesome in Accordion component.

{% tab template="accordion/accordion-font-awesome", es5Template="es5_font_awesome", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import {Accordion} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let accordion: Accordion = new Accordion({
    items: [
      { header: 'Twitter', expanded: 'true',  iconCss: 'fa fa-twitter' content: 'Twitter is an online social networking service that enables users to send and read short 140-character messages called "tweets".' },
      { header: 'Facebook',  iconCss: 'fa fa-facebook' content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates.' },
      { header: 'WhatsApp', iconCss: 'fa fa-whatsapp'  content: 'WhatsApp is an American freeware, cross-platform messaging and Voice over IP (VoIP) service owned by Facebook, Inc.' }
    ]
});
accordion.appendTo('#element');
```

{% endtab %}

## Customization

Use following CSS to customize the accordion items header icons.

```CSS

.e-accordion .e-acrdn-item .e-acrdn-header .e-acrdn-header-icon {
         display: inline-block;
         padding: 0 10px 0 0 !important;
}

```

Use following CSS to customize the selected accordion item content icons.

```CSS

.e-accordion .e-acrdn-item.e-select .e-acrdn-panel .e-acrdn-content .e-content-icon {
    color: rgba(0, 0, 0, 0.54) !important;
}

```