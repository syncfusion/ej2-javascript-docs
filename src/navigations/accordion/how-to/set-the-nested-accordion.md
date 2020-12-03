---
title: "Set the nested accordion"
component: "Accordion"
description: "This example demonstrates how to create an Essential JS 2 Accordion component inside another Essential JS 2 Accordion component."
---

# Set the nested Accordion

Accordion supports to render `nested` level of Accordion by using content property. You can give nested Accordion content inside the parent Accordion content property by using `id` of nested element. The nested Accordion can be rendered with the use of provided events, such as [`clicked`](../../api/accordion#clicked) and [`expanding`](../../api/accordion#expanding).

{% tab template="accordion/accordion", es5Template="es5_accordion_nested", sourceFiles="index.ts,index.html" %}

```typescript
import { Accordion, AccordionClickArgs, ExpandEventArgs } from '@syncfusion/ej2-navigations';

let nestAcrdn_vid: Accordion;
let nestAcrdn_mus: Accordion;
let nestAcrdn_musNew: Accordion;
let nestAcrdn_img: Accordion;
let accordion: Accordion = new Accordion({
  expanding: expanding,
  items: [
    { header: 'Video', content: '<div id="nested_video"></div>' },
    { header: 'Music', content: '<div id="nested_music"></div>' },
    { header: 'Images', content: '<div id="nested_images"></div>' },
  ]
});
accordion.appendTo('#element');
function clicked(e: AccordionClickArgs): void {
  let ele: HTMLElement = e.originalEvent.target;
  if (ele.querySelectorAll('.e-accordion').length > 0) {
    return;
  }
  if (!document.getElementById("nested_musicNew").classList.contains("e-accordion")) {
  nestAcrdn_musNew = new Accordion({
    items: [
      { header: 'New Track1' },
      { header: 'New Track2' }
    ]
  }, '#nested_musicNew');
  }
}

function expanding(e: ExpandEventArgs): void {
  if (e.isExpanded && [].indexOf.call(this.items, e.item) === 0) {
    if (e.element.querySelectorAll('.e-accordion').length > 0) {
      return;
    }
  nestAcrdn_vid = new Accordion({
    items: [
      { header: 'Video Track1' },
      { header: 'Video Track2' }
    ]
  }, '#nested_video');
  }
  if (e.isExpanded && [].indexOf.call(this.items, e.item) === 1) {
    if (e.element.querySelectorAll('.e-accordion').length > 0) {
      return;
    }
    nestAcrdn_mus = new Accordion({
      clicked: clicked,
      items: [
        { header: 'Music Track1' },
        { header: 'Music Track2' },
        { header: 'Music New', content: '<div id="nested_musicNew"></div>' }
      ]
    }, '#nested_music');
  }
  if (e.isExpanded && [].indexOf.call(this.items, e.item) === 2) {
    if (e.element.querySelectorAll('.e-accordion').length > 0) {
      return;
    }
    nestAcrdn_img = new Accordion({
      items: [
        { header: 'Track1' },
        { header: 'Track2' },
      ]
    }, '#nested_images');
  }
}

```

{% endtab %}