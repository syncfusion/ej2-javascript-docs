---
title: "Migration from Essential JS 1"
component: "Tab"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially."
---

# Migration from Essential JS 1

This article describes the API migration process of Tab component from Essential JS 1 to Essential JS 2.

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Keyboard Navigation | **Property:** *allowKeyboardNavigation* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; allowKeyboardNavigation: false <br /> }); <br /> | **Not Applicable** |
| Localization | **Not Applicable** | **Property:** *locale* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; locale: 'en-US' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| RTL | **Property:** *enableRTL* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enableRTL: false <br /> }); <br /> | **Property:** *enableRtl* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; enableRtl: false <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |

## AjaxSettings

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Property:** *ajaxSettings* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { type: 'GET' } <br /> }); <br /> | **Not Applicable** |
| Asynchronous | **Property:** *ajaxSettings.async* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { async: true } <br /> }); <br /> | **Not Applicable** |
| Browser Cache | **Property:** *ajaxSettings.cache* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { cache: false } <br /> }); <br /> | **Not Applicable** |
| Request type | **Property:** *ajaxSettings.contentType* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { contentType: "html" } <br /> }); <br /> | **Not Applicable** |
| Data | **Property:** *ajaxSettings.data* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { data: {} } <br /> }); <br /> | **Not Applicable** |
| Response type | **Property:** *ajaxSettings.dataType* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { dataType: "html" } <br /> }); <br /> | **Not Applicable** |
| HTTP request type | **Property:** *ajaxSettings.type* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSettings: { type: 'GET' } <br /> }); <br /> | **Not Applicable** |
| AjaxBeforeLoad | **Event:** *ajaxBeforeLoad* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxBeforeLoad: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxError | **Event:** *ajaxError* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxError: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxLoad | **Event:** *ajaxLoad* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxLoad: function(args) {} <br /> }); <br /> | **Not Applicable** |
| AjaxSuccess | **Event:** *ajaxSuccess* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; ajaxSuccess: function(args) {} <br /> }); <br /> | **Not Applicable** |

## Animation

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Not Applicable** | **Property:** *animation* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { prev: { }, next: { } } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| EnableAnimation | **Property:** *enableAnimation* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enableAnimation: false <br /> }); <br /> | **Not Applicable** |
| Previous animation | **Not Applicable** | **Property:** *animation.prev* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; prev: { <br /> &nbsp; &nbsp; &nbsp; duration: 400, <br /> &nbsp; &nbsp; &nbsp; easing: 'ease-in', <br /> &nbsp; &nbsp; &nbsp; effect: 'SlideLeft' <br /> &nbsp; &nbsp; } <br /> &nbsp; } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Next animation | **Not Applicable** | **Property:** *animation.next* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; next: { <br /> &nbsp; &nbsp; &nbsp; duration: 400, <br /> &nbsp; &nbsp; &nbsp; easing: 'ease-in', <br /> &nbsp; &nbsp; &nbsp; effect: 'SlideLeft' <br /> &nbsp; &nbsp; } <br /> &nbsp; } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Duration <br /> [prev / next] | **Not Applicable** | **Property:** *animation.next.duration* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; prev: { duration: 400 } <br /> &nbsp; } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Easing <br /> [prev / next] | **Not Applicable** | **Property:** *animation.next.easing* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; prev: { easing: 'ease-in' } <br /> &nbsp; } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Effect <br /> [prev / next] | **Not Applicable** | **Property:** *animation.next.effect* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; animation: { <br /> &nbsp; &nbsp; prev: { effect: 'SlideLeft' } <br /> &nbsp; } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |

## Header

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Header position | **Property:** *headerPosition* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; headerPosition: "Bottom" <br /> }); <br /> | **Property:** *headerPlacement* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; headerPlacement: 'Bottom' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Header size | **Property:** *headerSize* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; headerSize: "100px" <br /> }); <br /> | **Not Applicable** |
| OverflowModes | **Not Applicable** | **Property:** *overflowMode* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; overflowMode: 'Popup' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| TabScroll | **Property:** *enableTabScroll* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enableTabScroll: false <br /> }); <br /> | **Not Applicable** |

## Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Not Applicable** | **Property:** *items* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [] <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Content | **Not Applicable** | **Property:** *items[0].content* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; content: 'content1' <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Custom Class | **Not Applicable** | **Property:** *items[0].cssClass* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; cssClass: 'customClass' <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Header | **Not Applicable** | **Property:** *items[0].header* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; header: { } <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Icon class | **Not Applicable** | **Property:** *items[0].header.iconCss* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; header: { iconCss: 'e-icon' } <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Icon position | **Not Applicable** | **Property:** *items[0].header.iconPosition* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; header: { iconPosition: 'Left' } <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Header text | **Not Applicable** | **Property:** *items[0].header.text* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; header: { text: 'Tab1' } <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Get items length | **Method:** *getItemsCount()* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.getItemsCount(); <br /> | **Not Applicable** |
| Add Items | **Method:** *addItem(url, displayLabel, index, cssClass, id)* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.addItem("#new", "New Item", 3, "myClass", "newItem"); <br /> | **Method:** *addTab(items, index)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.addTab([{ <br /> &nbsp; header: { text: 'Tab1' }, <br /> &nbsp; content: 'contents' }], 1 <br /> ); <br /> |
|  BeforeAdd | **Not Applicable** | **Event:** *adding* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; adding: function(e: Event): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| AfterAdd | **Event:** *itemAdd* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; itemAdd: function(args) {} <br /> }); <br /> | **Event:** *added* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; added: function(e: Event): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Remove item | **Method:** *removeItem(index)* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.removeItem(1); <br /> | **Method:** *removeTab(index)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.removeTab(1); <br /> |
| BeforeRemove | **Event:** *beforeItemRemove* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; beforeItemRemove: function(args) {} <br /> }); <br /> | **Event:** *removing* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; removing: function(e: RemoveEventArgs): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| AfterRemove | **Event:** *itemRemove* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; itemRemove: function(args) {} <br /> }); <br /> | **Event:** *removed* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; removed: function(e: RemoveEventArgs): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| SelectedItemIndex | **Property:** *selectedItemIndex* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; selectedItemIndex : 1 <br /> }); <br /> | **Property:** *selectedItem* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; selectedItem: 0 <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Select item | **Not Applicable** | **Method:** *select(index)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.select(1); <br /> |
| BeforeActive | **Event:** *beforeActive* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; beforeActive: function(args) {} <br /> }); <br /> | **Event:** *selecting* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; selecting: function(e: SelectEventArgs): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| AfterActive | **Event:** *itemActive* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; itemActive: function(args) {} <br /> }); <br /> | **Event:** *selected* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; selected: function(e: SelectEventArgs): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Disable items | **Property:** *disabledItemIndex* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; disabledItemIndex: [1, 2] <br /> }); <br /> | **Not Applicable** |
| Enable items | **Property:** *enabledItemIndex* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enabledItemIndex: [1, 2] <br /> }); <br /> | **Not Applicable** |
| Enable/Disable item | **Not Applicable** | **Property:** *items[0].disabled* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; items: [ { <br /> &nbsp;&nbsp; disabled: true <br /> &nbsp; } ]<br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Hide items | **Property:** *hiddenItemIndex* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; hiddenItemIndex: [1, 2] <br /> }); <br /> | **Not Applicable** |
| Hide item | **Method:** *hideItem(index)* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.hideItem(1); <br /> | **Method:** *hideTab(index, true)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.hideTab(1, true); <br /> |
| Show item | **Method:** *showItem(index)* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.showItem(1); <br /> | **Method:** *hideTab(index, false)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.hideTab(1, false); <br /> |

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Collapse active item | **Property:** *collapsible* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; collapsible: true <br /> }); <br /> | **Not Applicable** |
| Custom class | **Property:** *cssClass* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; cssClass: 'customClass' <br /> }); <br /> | **Property:** *cssClass* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; cssClass: 'customClass' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Enabled | **Property:** *enabled* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enabled: false <br /> }); <br /> | **Method:** *disable(false)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.disable(false); <br /> |
| Persistence | **Property:** *enablePersistence* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; enablePersistence: false <br /> }); <br /> | **Property:** *enablePersistence* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; enablePersistence: false <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Events | **Property:** *events* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; events: "click" <br /> }); <br /> | **Not Applicable** |
| Height | **Property:** *height* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; height: "100%" <br /> }); <br /> | **Property:** *height* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; height: '100%' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| HeightAdjustMode | **Property:** *heightAdjustMode* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; heightAdjustMode : ej.Tab.HeightAdjustMode.Content <br /> }); <br /> | **Property:** *heightAdjustMode* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; heightAdjustMode: 'Content' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| HTML Attributes | **Property:** *htmlAttributes* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; htmlAttributes: { class: "my-class" } <br /> }); <br /> | **Not Applicable** |
| ID prefix | **Property:** *idPrefix* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; idPrefix: "ej-tab-" <br /> }); <br /> | **Not Applicable** |
| ShowCloseButton | **Property:** *showCloseButton* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; showCloseButton : true <br /> }); <br /> | **Property:** *showCloseButton* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; showCloseButton: true <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| showReloadIcon | **Property:** *showReloadIcon* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; showReloadIcon : true <br /> }); <br /> | **Not Applicable** |
| ShowRoundedCorner | **Property:** *showRoundedCorner* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; showRoundedCorner : true <br /> }); <br /> | **Not Applicable** |
| Width | **Property:** *width* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; width: "100%" <br /> }); <br /> | **Property:** *width* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; width: '100%' <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Destroy | **Not Applicable** | **Method:** *destroy()* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab');<br /> tab.destroy(); <br /> |
| Disable Tab | **Method:** *disable()* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.disable(); <br /> | **Method:** *disable(true)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.disable(true); <br /> |
| Enable Tab | **Method:** *enable()* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.enable(); <br /> | **Method:** *disable(false)* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab'); <br /> tab.disable(false); <br /> |
| Hide Tab | **Method:** *hide()* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.hide(); <br /> | **Not Applicable** |
| Refresh | **Not Applicable** | **Method:** *refresh()* <br /><br /> var tab = new ej.navigations.Tab(); <br /> tab.appendTo('#ej2Tab');<br /> tab.refresh(); <br /> |
| Show Tab | **Method:** *show()* <br /><br /> $("#tab").ejTab(); <br /> var tabObj = $("#tab").data("ejTab"); <br /> tabObj.show(); <br /> | **Not Applicable** |
| Created | **Event:** *create* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; create: function(args) {} <br /> }); <br /> | **Event:** *created* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; created: function(e: Event): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |
| Destroyed | **Event:** *destroy* <br /><br /> $("#tab").ejTab({ <br /> &nbsp; destroy: function(args) {} <br /> }); <br /> | **Event:** *destroyed* <br /><br /> var tab = new ej.navigations.Tab({ <br /> &nbsp; destroyed: function(e: Event): void { } <br /> }); <br /> tab.appendTo('#ej2Tab'); <br /> |