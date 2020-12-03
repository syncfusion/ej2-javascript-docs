---
title: "Migration from Essential JS 1"
component: "Menu"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, menu component."
---

# Migration from Essential JS 1

This article describes the API migration process of Menu component from Essential JS 1 to Essential JS 2.

## Properties

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Animation type on hover or click on the menu items | **Property:** *animationType* <br/><br/> $("#menu").ejMenu({ <br/>animationType: ej.AnimationType.Default <br/> }); | Not applicable |
| Context menu target  | **Property:** *contextMenuTarget* <br/><br/> $("#menu").ejMenu({ <br/>menuType: ej.MenuType.ContextMenu, <br/>contextMenuTarget: "#target", <br/> }); | Not applicable |
| Container element for submenu’s collision | **Property:** *container* <br/><br/> $("#menu").ejMenu({ <br/> container: "#target", <br/> target: "#target"<br/> }); | Not applicable |
| Menu items  | Not applicable | **Property:** *items* <br/> var menu = new ej.navigations.Menu({ <br/>items: menuItems<br/>}); <br/>menu.appendTo("#menu"); <br/> var menuItems = [ <br/> &nbsp; {<br/> &nbsp; &nbsp; text: 'File'  &nbsp; <br/> &nbsp; }, <br/> &nbsp; {<br/> &nbsp; &nbsp; text: 'Edit'  &nbsp; <br/> &nbsp; }, <br/> &nbsp; {<br/> &nbsp; &nbsp; text: 'More' <br/> &nbsp; }, <br/> &nbsp; {<br/> &nbsp; &nbsp; text: 'Help'  &nbsp; <br/> &nbsp; } <br/> ] |
| Adding custom class  | **Property:** *cssClass* <br/><br/> $("#menu").ejMenu({ <br/>cssClass: "e-custom-class" <br/> }); | **Property:** *cssClass* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>cssClass: "e-custom-class",<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Enables or disables the animation on hover or click on the menu items | **Property:** *enableAnimation* <br/><br/> $("#menu").ejMenu({ <br/>enableAnimation: true, <br/> }); | Not applicable |
| Root menu items to be aligned center in horizontal menu | **Property:** *enableCenterAlign* <br/><br/> $("#menu").ejMenu({ <br/>enableCenterAlign: true, <br/> }); | Not applicable |
| Disabled state | **Property:** *enabled* <br/><br/> $("#menu").ejMenu({ <br/>enabled: false <br/> }); | **Property:** *disabled* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>disabled: true,<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| RTL  | **Property:** *enableRTL* <br/><br/> $("#menu").ejMenu({ <br/>enableRTL: true <br/> }); | **Property:** *enableRtl* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>enableRtl: true,<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Enables/Disables the separator  | **Property:** *enableSeparator* <br/><br/> $("#menu").ejMenu({ <br/>enableSeparator: true <br/> }); | Not applicable |
| Exclude target for context menu  | **Property:** *excludeTarget* <br/><br/> $("#menu").ejMenu({ <br/>excludeTarget: ".exclude-target",<br/>menuType: ej.MenuType.ContextMenu, <br/> contextMenuTarget: "#target" <br/> }); | Not applicable |
| Fields | **Property:** *fields* <br/><br/> $("#menu").ejMenu({ <br/>fields: menuFields <br/> }); | **Property:** *fields* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>fields: menuFields,<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Height | **Property:** *height* <br/><br/> $("#menu").ejMenu({ <br/>height: "25" <br/> }); | Not applicable |
| HTML Attributes | **Property:** *htmlAttributes* <br/><br/> $("#menu").ejMenu({ <br/>htmlAttributes: {"aria-label":"menu"} <br/> }); | Not applicable |
| Responsive | **Property:** *isResponsive* <br/><br/> $("#menu").ejMenu({ <br/>isResponsive: true<br/> }); | Not applicable |
| Menu Type | **Property:** *menuType* <br/><br/> $("#menu").ejMenu({ <br/>menuType: ej.MenuType.ContextMenu, <br/>contextMenuTarget: "#target"<br/> }); | Not applicable |
| Show item on click  | **Property:** *openOnClick* <br/><br/> $("#menu").ejMenu({ <br/>openOnClick: true <br/> }); | **Property:** *showItemOnClick* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>showItemOnClick: true,<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Orientation  | **Property:** *orientation* <br/><br/> $("#menu").ejMenu({ <br/>orientation: ej.Orientation.Vertical <br/> }); | **Property:** *orientation* <br/><br/>  var menu = new ej.navigations.Menu({ <br/>orientation: "Vertical",<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Show root level arrows | **Property:** *showRootLevelArrows* <br/><br/> $("#menu").ejMenu({ <br/>showRootLevelArrows: false<br/> }); | Not applicable |
| Show sub level arrows | **Property:** *showSubLevelArrows* <br/><br/> $("#menu").ejMenu({ <br/>showSubLevelArrows: false<br/> }); | Not applicable |
| Sub menu direction | **Property:** *subMenuDirection* <br/><br/> $("#menu").ejMenu({ <br/>subMenuDirection: "left"<br/> }); | Not applicable |
| Title | **Property:** *titleText* <br/><br/> $("#menu").ejMenu({ <br/>titleText: "Menu"<br/> }); | Not applicable |
| Width | **Property:** *width* <br/><br/> $("#menu").ejMenu({ <br/>width: "800px"<br/> }); | Not applicable |
| Animation settings  | Not applicable | **Property:** *animationSettings* <br/><br/> let animationSettings: MenuAnimationSettings = { effect: "FadeIn" }<br/> var menu = new ej.navigations.Menu({ <br/>animationSettings: animationSettings,<br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu"); |
| Template  | Not applicable | **Property:** *template* <br/><br/>  var menu = new ej.navigations.Menu({<br/>items: [{<br/> category: 'Services', options: [{<br/> suport: [<br/> { value: 'Application Development', count: '1200+' },<br/>{ value: 'Maintenance & Support', count: '3700+' },<br/>{ value: 'Quality Assurance' }<br/>]<br/>}]<br/>}<br/>{ category: 'Careers' },<br/>{ category: 'Sign In' }<br/>],<br/>template: "#template"}); <br/>menu.appendTo("#menu"); |
| Pop up menu height | **Property:** *overflowHeight* <br/><br/> $("#menu").ejMenu({ <br/>overflowHeight: "200px"<br/> }); | Not applicable |

## Methods

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Disable Method | **Method:** *disable* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.disable();| Not applicable |
| Disable menu items | **Method:** *disableItem* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.disableItem("Home");| **Method:** *enableItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.enableItems("Home", false) |
| Disable menu items by ID | **Method:** *disableItemByID* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.disableItemByID("home_id"); | **Method:** *enableItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.enableItems("home_id", false, true) |
| Enable Method | **Method:** *enable* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.enable();| Not applicable |
| Enable menu items | **Method:** *enableItem* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.enableItem("Home");| **Method:** *enableItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.enableItems("Home", true); |
| Enable menu items by ID | **Method:** *enableItemByID* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.enableItemByID("home_id");| **Method:** *enableItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.enableItems("home_id", true, true); |
| Hide Method | **Method:** *hide* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.hide(); | Not applicable |
| Hide menu items | **Method:** *hideItems* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.hideItems(["#search","#company"]); | **Method:** *hideItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.hideItems(["search","company"], true); |
| Insert menu items | **Method:** *insert* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.insert([{ id: "More", text: "More" }], "#Home");| Not applicable |
| Insert menu items after the specified menu item | **Method:** *insertAfter* <br/><br/> $("#menu").ejMenu({ }); <br/> menu.insertAfter([{ id: "More", text: "More" }], "#Home");| **Method:** *insertAfter* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.insertAfter([{ id: "More", text: "More" }], "Home"); |
| Insert menu items before the specified menu item | **Method:** *insertBefore* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.insertBefore([{ id: "More", text: "More" }], "#Home"); | **Method:** *insertBefore* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.insertBefore([{ id: "More", text: "More" }], "Home"); |
| Remove menu items | **Method:** *remove* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.remove(["#Home"]);| **Method:** *removeItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/> menu.appendTo("#menu"); <br/> menu.removeItems(["Home"]); |
| To show menu | **Method:** *show* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.show();| Not applicable |
| To show menu items | **Method:** *showItems* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.showItems(["#search", "#company"]);| **Method:** *showItems* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/>menu.appendTo("#menu");<br/> menu.showItems(["Search", "Company"]); |
| Destroy method | **Method:** *destroy* <br/><br/> $("#menu").ejMenu({ }); <br/> var menu = $("#menu").data("ejMenu"); <br/> menu.destroy();| **Method:** *destroy* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems<br/>}); <br/> menu.appendTo("#menu");<br/> menu.destroy(); |

## Events

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Triggers before opening the menu | **Events:** *beforeOpen* <br/><br/> $("#menu").ejMenu({<br/> beforeOpen: function(args) { /** code block */ } <br/> }); | **Events:** *beforeOpen* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> beforeOpen: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers before closing the menu | Not applicable | **Events:** *beforeClose* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> beforeClose: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers before rendering each menu item | Not applicable | **Events:** *beforeItemRender* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> beforeItemRender: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers while selecting the menu item | **Events:** *click* <br/><br/> $("#menu").ejMenu({<br/> click: function(args) { /** code block */ } <br/> }); | **Events:** *select* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> select: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers after closing the menu | **Events:** *close* <br/><br/> $("#menu").ejMenu({<br/> close: function(args) { /** code block */ } <br/> }); | **Events:** *onClose* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> onClose: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers after opening the menu | **Events:** *open* <br/><br/> $("#menu").ejMenu({<br/> open: function(args) { /** code block */ } <br/> }); | **Events:** *onOpen* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> onOpen: function(args) { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers once the component rendering is completed | **Events:** *create* <br/><br/> $("#menu").ejMenu({<br/> create: function(args) { /** code block */ } <br/> }); | **Events:** *created* <br/><br/>  var menu = new ej.navigations.Menu({ <br/> items: menuItems <br/> created: function() { /** code block */ }<br/>}); <br/>menu.appendTo("#menu"); |
| Triggers once the component is destroyed | **Events:** *destroy* <br/><br/> $("#menu").ejMenu({<br/> destroy: function(args) { /** code block */ } <br/> }); | Not applicable |
| Triggers when key down on menu items | **Events:** *keydown* <br/><br/> $("#menu").ejMenu({<br/> keydown: function(args) { /** code block */ } <br/> }); | Not applicable |
| Triggers when mouse out from menu items | **Events:** *mouseout* <br/><br/> $("#menu").ejMenu({<br/> mouseout: function(args) { /** code block */ } <br/> }); | Not applicable |
| Triggers when mouse over the Menu items | **Events:** *mouseover* <br/><br/> $("#menu").ejMenu({<br/> mouseover: function(args) { /** code block */ } <br/> }); | Not applicable |
| Triggers when overflow popup menu opens | **Events:** *overflowOpen* <br/><br/> $("#menu").ejMenu({<br/> overflowOpen: function(args) { /** code block */ } <br/> }); | Not applicable |
| Triggers when overflow popup menu closes | **Events:** *overflowClose* <br/><br/> $("#menu").ejMenu({<br/> overflowClose: function(args) { /** code block */ } <br/> }); | Not applicable |