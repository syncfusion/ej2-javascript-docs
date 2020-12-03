---
title: "Migration from Essential JS 1"
component: "Accordion"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components."
---

# Migration from Essential JS 1

This article describes the API migration process of Accordion component from Essential JS 1 to Essential JS 2.

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Keyboard Navigation | **Property:** *allowKeyboardNavigation* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; allowKeyboardNavigation: false <br /> }); <br /> | **Not Applicable** |
| Localization | **Not Applicable** | **Property:** *locale* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; locale: 'en-US' <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| RTL | **Property:** *enableRTL* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; enableRTL: false <br /> }); <br /> | **Property:** *enableRtl* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; enableRtl: false <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |

## AjaxSettings

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Property:** *ajaxSettings* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { type: 'GET' } <br /> }); <br /> | **Not Applicable** |
| Asynchronous | **Property:** *ajaxSettings.async* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { async: true } <br /> }); <br /> | **Not Applicable** |
| Browser Cache | **Property:** *ajaxSettings.cache* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { cache: false } <br /> }); <br /> | **Not Applicable** |
| Request type | **Property:** *ajaxSettings.contentType* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { contentType: "html" } <br /> }); <br /> | **Not Applicable** |
| Data | **Property:** *ajaxSettings.data* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { data: {} } <br /> }); <br /> | **Not Applicable** |
| Response type | **Property:** *ajaxSettings.dataType* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { dataType: "html" } <br /> }); <br /> | **Not Applicable** |
| HTTP request type | **Property:** *ajaxSettings.type* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSettings: { type: 'GET' } <br /> }); <br /> | **Not Applicable** |
| AjaxBeforeLoad | **Event:** *ajaxBeforeLoad* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxBeforeLoad: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxError | **Event:** *ajaxError* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxError: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxLoad | **Event:** *ajaxLoad* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxLoad: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxSuccess | **Event:** *ajaxSuccess* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; ajaxSuccess: function(args) {} <br /> }); <br /> | **Not Applicable** |

## Animation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Not Applicable** | **Property:** *animation* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { expand: { }, collapse: { } } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| EnableAnimation | **Property:** *enableAnimation* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; enableAnimation: false <br /> }); <br /> | **Not Applicable** |
| Expand animation | **Not Applicable** | **Property:** *animation.expand* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; expand: { <br /> &nbsp; &nbsp; &nbsp; duration: 400, <br /> &nbsp; &nbsp; &nbsp; easing: 'ease-in', <br /> &nbsp; &nbsp; &nbsp; effect: 'SlideLeft' <br /> &nbsp; &nbsp; } <br /> &nbsp; } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Collapse animation | **Not Applicable** | **Property:** *animation.collapse* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; collapse: { <br /> &nbsp; &nbsp; &nbsp; duration: 400, <br /> &nbsp; &nbsp; &nbsp; easing: 'ease-in', <br /> &nbsp; &nbsp; &nbsp; effect: 'SlideLeft' <br /> &nbsp; &nbsp; } <br /> &nbsp; } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Duration <br /> [expand / collapse] | **Not Applicable** | **Property:** *animation.collapse.duration* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; expand: { duration: 400 } <br /> &nbsp; } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Easing <br /> [expand / collapse] | **Not Applicable** | **Property:** *animation.collapse.easing* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; expand: { easing: 'ease-in' } <br /> &nbsp; } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Effect <br /> [expand / collapse] | **Not Applicable** | **Property:** *animation.collapse.effect* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; expand: { effect: 'SlideLeft' } <br /> &nbsp; } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |

## Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Not Applicable** | **Property:** *items* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Content | **Not Applicable** | **Property:** *items[0].content* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [{ content: 'Contents' }] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Custom class | **Not Applicable** | **Property:** *items[0].cssClass* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [{ cssClass: 'customClass' }] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Header | **Not Applicable** | **Property:** *items[0].header* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [{ header: 'Header1' }] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| HeaderSize | **Property:** *headerSize* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; headerSize: '50px' <br /> }); <br /> | **Not Applicable** |
| Icon class | **Not Applicable** | **Property:** *items[0].iconCss* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [{ iconCss: 'e-icons' }] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| IsExpand | **Not Applicable** | **Property:** *items[0].expanded* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; items: [{ expanded: true }] <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Collapse Item | **Method:** *collapsePanel(index)* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.collapsePanel(0); <br /> | **Method:** *expandItem(index, false)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.expandItem(0, false); <br /> |
| Expand Item | **Method:** *expandPanel(index)* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.expandPanel(0); <br /> | **Method:** *expandItem(index, true)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.expandItem(0, true); <br /> |
| CollapseAll | **Method:** *collapseAll()* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.collapseAll(); <br /> | **Not Applicable** |
| ExpandAll | **Method:** *expandAll()* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.expandAll(); <br /> | **Not Applicable** |
| Get ItemsCount | **Method:** *getItemsCount()* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.getItemsCount(); <br /> | **Not Applicable** |
| AddItem | **Method:** *addItem(text, content, index)* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.addItem("New item", "The accordion content", 2); <br /> | **Method:** *addItem(items, index)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.addItem([{ header: 'App', content: 'text' }], 0) <br /> |
| Remove Item | **Method:** *removeItem(index)* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.removeItem(0); <br /> | **Method:** *removeItem(index)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.removeItem(0) <br /> |
| Disable Items | **Property:** *disablesItems* <br /><br /> $("#accordion").ejTab({ <br /> &nbsp; disabledItems: [0, 1] <br /> }); <br /> | **Not Applicable** |
| Enable Items | **Property:** *enabledItems* <br /><br /> $("#accordion").ejTab({ <br /> &nbsp; enabledItems: [0, 1] <br /> }); <br /> | **Not Applicable** |
| Disable Item | **Method:** *disableItems([index])* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.disableItems([1]); <br /> | **Method:** *enableItem(index, false)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.enableItem(0, false) <br /> |
| Enable Item | **Method:** *enableItems([index])* <br /><br /> $("#accordion").ejTab(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.enableItems([1]); <br /> | **Method:** *enableItem(index, true)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.enableItem(0, true) <br /> |
| Hide Item | **Not Applicable** | **Method:** *hideItem(index, true)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.hideItem(0, true) <br /> |
| SelectedItemIndex | **Property:** *selectedItemIndex* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; selectedItemIndex: false <br /> }); <br /> | **Not Applicable** |
| Select | **Not Applicable** | **Method:** *select(index)* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.select(0) <br /> |
| BeforeActivate | **Event:** *beforeActivate* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; beforeActivate: function(args) {} <br /> }); <br /> | **Event:** *expanding* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; expanding: function(e: Event): void { } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Activate | **Event:** *activate* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; activate: function(args) {} <br /> }); <br /> | **Event:** *expanded* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; expanded: function(e: Event): void { } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| beforeInActivate | **Event:** *beforeInactivate* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; beforeInactivate: function(args) {} <br /> }); <br /> | **Not Applicable** |
| InActive | **Event:** *inActivate* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; inActivate: function(args) {} <br /> }); <br /> | **Not Applicable** |
| Clicked | **Not Applicable** | **Event:** *clicked* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; clicked: function(e: Event): void { } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Collapsible | **Property:** *collapsible* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; collapsible: false <br /> }); <br /> | **Not Applicable** |
| Collapse speed | **Property:** *collapseSpeed* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; collapseSpeed: 500 <br /> }); <br /> | **Not Applicable** |
| Custom class | **Property:** *cssClass* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; cssClass: 'custom' <br /> }); <br /> | **Not Applicable** |
| CustomIcon class | **Property:** *customIcon* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; customIcon: { <br /> &nbsp; &nbsp; header: "header-close", <br /> &nbsp; &nbsp; selectedHeader: "header-expand" <br /> &nbsp; } <br /> }); <br /> | **Not Applicable** |
| Enabled | **Property:** *enabled* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; enabled: false <br /> }); <br /> | **Not Applicable** |
| Events | **Property:** *events* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; events: "mouseover" <br /> }); <br /> | **Not Applicable** |
| Expand speed | **Property:** *expandSpeed* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; expandSpeed: 300 <br /> }); <br /> | **Not Applicable** |
| Height | **Property:** *height* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; height: 400 <br /> }); <br /> | **Property:** *height* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; height: 700 <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| HeightAdjustMode | **Property:** *heightAdjustMode* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; heightAdjustMode: "content" <br /> }); <br /> | **Not Applicable** |
| HtmlAttributes | **Property:** *htmlAttributes* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; htmlAttributes: { title: "Demo" } <br /> }); <br /> | **Not Applicable** |
| MultipleOpen | **Property:** *enableMultipleOpen* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; enableMultipleOpen: true <br /> }); <br /> | **Property:** *expandMode* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; expandMode: 'Multiple' <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Persistence | **Property:** *enablePersistence* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; enablePersistence: false <br /> }); <br /> | **Property:** *enablePersistence* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; enablePersistence: true <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| ShowRounderCorner | **Property:** *showRoundedCorner* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; showRoundedCorner: false <br /> }); <br /> | **Not Applicable** |
| Width | **Property:** *width* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; width: 600 <br /> }); <br /> | **Property:** *width* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; width: 500 <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Enable | **Method:** *enable()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.enable(); <br /> | **Not Applicable** |
| Disable | **Method:** *disable()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.disable(); <br /> | **Not Applicable** |
| Show | **Method:** *show()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.show(); <br /> | **Not Applicable** |
| Hide | **Method:** *hide()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.hide(); <br /> | **Not Applicable** |
| Destroy | **Method:** *destroy()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.destroy(); <br /> | **Method:** *destroy()* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.destroy(); <br /> |
| Refresh | **Method:** *refresh()* <br /><br /> $("#accordion").ejAccordion(); <br /> var accordion = $("#accordion").data("ejAccordion"); <br /> accordion.refresh(); <br /> | **Method:** *refresh()* <br /><br /> var accordion = new ej.navigations.Accordion(); <br /> accordion.appendTo('#ej2Accordion'); <br /> accordion.refresh(); <br /> |
| Created | **Event:** *create* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; create: function(args) {} <br /> }); <br /> | **Event:** *created* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; created: function(e: Event): void { } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |
| Destroyed | **Event:** *destroy* <br /><br /> $("#accordion").ejAccordion({ <br /> &nbsp; destroy: function(args) {} <br /> }); <br /> | **Event:** *destroyed* <br /><br /> var accordion = new ej.navigations.Accordion({ <br /> &nbsp; destroyed: function(e: Event): void { } <br /> }); <br /> accordion.appendTo('#ej2Accordion'); <br /> |