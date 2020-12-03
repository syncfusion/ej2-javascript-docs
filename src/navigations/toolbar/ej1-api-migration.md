---
title: "Migration from Essential JS 1"
component: "Toolbar"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components."
---

# Migration from Essential JS 1

This article describes the API migration process of Toolbar component from Essential JS 1 to Essential JS 2.

## Accessibility

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Localization | **Not Applicable** | **Property:** *locale* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; locale: 'en-US' <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| RTL | **Property:** *enableRTL* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; enableRTL: true <br /> }); <br /> | **Property:** *enableRtl* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; enableRtl: true <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |

## DataSource

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| DataSource | **Property:** *dataSource* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; dataSource: items <br /> }); <br /> | **Not Applicable** |
| Query | **Property:** *query* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; query: query <br /> }); <br /> | **Not Applicable** |
| Fields | **Property:** *fields* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: {} <br /> }); <br /> | **Not Applicable** |
| Group | **Property:** *group* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { group: '' } <br /> }); <br /> | **Not Applicable** |
| HtmlAttributes | **Property:** *htmlAttributes* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { htmlAttributes: {} } <br /> }); <br /> | **Not Applicable** |
| Id | **Property:** *id* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { id: '' } <br /> }); <br /> | **Not Applicable** |
| ImageAttributes | **Property:** *imageAttributes* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { imageAttributes: {} } <br /> }); <br /> | **Not Applicable** |
| ImageUrl | **Property:** *imageUrl* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { imageUrl: '' } <br /> }); <br /> | **Not Applicable** |
| SpriteCssClass | **Property:** *spriteCssClass* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { spriteCssClass: '' } <br /> }); <br /> | **Not Applicable** |
| Text | **Property:** *text* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { text: '' } <br /> }); <br /> | **Not Applicable** |
| TooltipText | **Property:** *tooltipText* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { tooltipText: '' } <br /> }); <br /> | **Not Applicable** |
| Template | **Property:** *template* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; fields: { template: '' } <br /> }); <br /> | **Not Applicable** |

## Items

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Default | **Property:** *items* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [] <br /> }); <br /> | **Property:** *items* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Align | **Not Applicable** | **Property:** *items[0].align* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> items: [{ align: 'center' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Custom Class | **Not Applicable** | **Property:** *items[0].cssClass* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> items: [{ cssClass: 'e-class' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Group Name | **Property:** *items[0].group* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ group: '' }] <br /> }); <br /> | **Not Applicable** |
| Html Attributes | **Property:** *items[0].htmlAttributes* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ htmlAttributes: {} }] <br /> }); <br /> | **Property:** *items[0].htmlAttributes* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ htmlAttributes: {} }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Id | **Property:** *items[0].id* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ id: '' }] <br /> }); <br /> | **Property:** *items[0].id* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ id: '' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| ImageAttributes | **Property:** *items[0].imageAttributes* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ imageAttributes: {} }] <br /> }); <br /> | **Not Applicable** |
| ImageUrl | **Property:** *items[0].imageUrl* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ imageUrl: '' }] <br /> }); <br /> | **Not Applicable** |
| Overflow | **Not Applicable** | **Property:** *items[0].overflow* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ overflow: 'popup' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| PrefixIcon | **Not Applicable** | **Property:** *items[0].prefixIcon* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ prefixIcon: 'e-icon' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| ShowAlwaysInPopup | **Not Applicable** | **Property:** *items[0].showAlwaysInPopup* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ showAlwaysInPopup: true }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| ShowTextOn | **Not Applicable** | **Property:** *items[0].showTextOn* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ showTextOn: 'popup' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Sprite CssClass | **Property:** *items[0].spriteCssClass* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ spriteCssClass: 'e-class' }] <br /> }); <br /> | **Not Applicable** |
| SuffixIcon | **Not Applicable** | **Property:** *items[0].suffixIcon* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ suffixIcon: 'e-icon' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Template | **Property:** *items[0].template* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ template: '' }] <br /> }); <br /> | **Property:** *items[0].template* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ template: '' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Text | **Property:** *items[0].text* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ text: 'Cut' }] <br /> }); <br /> | **Property:** *items[0].text* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ text: 'Cut' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| TooltipText | **Property:** *items[0].tooltipText* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; items: [{ tooltipText: 'Cut' }] <br /> }); <br /> | **Property:** *items[0].tooltipText* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ tooltipText: 'Cut' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Type | **Not Applicable** | **Property:** *items[0].type* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ type: 'Button' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Width | **Not Applicable** | **Property:** *items[0].width* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; items: [{ width: '50' }] <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Disable Items | **Property:** *disabledItemIndices* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; disabledItemIndices: [] <br /> }); <br /> | **Method:** *enableItems(items, false)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.enableItems([], false); <br /> |
| Add Items | **Not Applicable** | **Method:** *addItems(items, index)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.addItems([], 0); <br /> |
| RemoveItem | **Method:** *removeItem(element)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.removeItem(ele); <br /> | **Method:** *removeItems(args)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.removeItems(0); <br /> |
| RemoveItemById | **Method:** *removeItemById(id)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.removeItemById('left'); <br /> | **Not Applicable** |
| Enable Item | **Method:** *enableItem(element)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.enableItem(ele); <br /> | **Method:** *enableItems(items, true)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.enableItems(items, true); <br /> |
| EnableItemById | **Method:** *enableItemById(id)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.enableItemById('left'); <br /> | **Not Applicable** |
| Disable Item | **Method:** *disableItem(element)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.disableItem(ele); <br /> | **Method:** *enableItems(items, false)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.enableItems([], false); <br /> |
| DisableItemById | **Method:** *disableItemById(id)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.disableItemById('left'); <br /> | **Not Applicable** |
| Show Item | **Not Applicable** | **Method:** *hideItem(index, false)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.hideItem(0, false); <br /> |
| Hide Item | **Not Applicable** | **Method:** *hideItem(index, true)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.hideItem(0, true); <br /> |
| SelectItem | **Method:** *selectItem(element)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.selectItem(ele); <br /> | **Not Applicable** |
| SelectItemById | **Method:** *selectItemById(id)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.selectItemById('left'); <br /> | **Not Applicable** |
| Deselect Item | **Method:** *deselectItem(element)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.deselectItem(ele); <br /> | **Not Applicable** |
| DeselectItemById | **Method:** *deselectItemById(id)* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.deselectItemById('left'); <br /> | **Not Applicable** |
| Clicked | **Not Applicable** | **Event:** *clicked* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; clicked: function(e: Event): void { } <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| itemHover | **Event:** *itemHover* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; itemHover: function(args) {} <br /> }); <br /> | **Not Applicable** |
| itemLeave | **Event:** *itemLeave* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; itemLeave: function(args) {} <br /> }); <br /> | **Not Applicable** |

## Common

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
| Custom class | **Property:** *cssClass* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; cssClass: 'customClass' <br /> }); <br /> | **Not Applicable** |
| Enabled | **Property:** *enabled* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; enabled: false <br /> }); <br /> | **Not Applicable** |
| EnableSeparator | **Property:** *enableSeparator* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; enableSeparator: false <br /> }); <br /> | **Not Applicable** |
| Height | **Property:** *height* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; height: 400 <br /> }); <br /> | **Property:** *height* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; height: 700 <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| HtmlAttributes | **Property:** *htmlAttributes* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; htmlAttributes: {} <br /> }); <br /> | **Not Applicable** |
| Hide | **Property:** *hide* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; hide: true <br /> }); <br /> | **Not Applicable** |
| Orientation | **Property:** *orientation* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; orientation: ej.Orientation.Horizontal <br /> }); <br /> | **Not Applicable** |
| OverflowModes | **Property:** *responsiveType* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; responsiveType: 'popup' <br /> }); <br /> | **Property:** *overflowMode* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; overflowMode: 'Popup' <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Persistence | **Not Applicable** | **Property:** *enablePersistence*  <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; enablePersistence: true <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Responsive | **Property:** *isResponsive* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; isResponsive: true <br /> }); <br /> | **Not Applicable** |
| ShowRounderCorner | **Property:** *showRoundedCorner* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; showRoundedCorner: false <br /> }); <br /> | **Not Applicable** |
| Width | **Property:** *width* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; width: 600 <br /> }); <br /> | **Property:** *width* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; width: 500 <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Enable | **Method:** *enable()* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.enable(); <br /> | **Method:** *disable(false)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.disable(false); <br /> |
| Disable | **Method:** *disable()* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.disable(); <br /> | **Method:** *disable(true)* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.disable(true); <br /> |
| Show | **Method:** *show()* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.show(); <br /> | **Not Applicable** |
| Hide | **Method:** *hide()* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.hide(); <br /> | **Not Applicable** |
| Refresh | **Not Applicable** | **Method:** *refresh()* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.refresh(); <br /> |
| Destroy | **Method:** *destroy()* <br /><br /> $("#toolbar").ejToolbar(); <br /> var toolbar = $("#toolbar").data("ejToolbar"); <br /> toolbar.destroy(); <br /> | **Method:** *destroy()* <br /><br /> var toolbar = new ej.navigations.Toolbar(); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> toolbar.destroy(); <br /> |
| Click | **Event:** *click* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; click: function(args) {} <br /> }); <br /> | **Not Applicable** |
| BeforeCreate | **Not Applicable** | **Event:** *beforeCreate* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; beforeCreate: function(e: Event): void { } <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Created | **Event:** *create* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; create: function(args) {} <br /> }); <br /> | **Event:** *created* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; created: function(e: Event): void { } <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| Destroyed | **Event:** *destroy* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; destroy: function(args) {} <br /> }); <br /> | **Event:** *destroyed* <br /><br /> var toolbar = new ej.navigations.Toolbar({ <br /> &nbsp; destroyed: function(e: Event): void { } <br /> }); <br /> toolbar.appendTo('#ej2Toolbar'); <br /> |
| FocusOut | **Event:** *focusOut* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; focusOut: function(args) {} <br /> }); <br /> | **Not Applicable** |
| overflowOpen | **Event:** *overflowOpen* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; overflowOpen: function(args) {} <br /> }); <br /> | **Not Applicable** |
| overflowClose | **Event:** *overflowClose* <br /><br /> $("#toolbar").ejToolbar({ <br /> &nbsp; overflowClose: function(args) {} <br /> }); <br /> | **Not Applicable** |