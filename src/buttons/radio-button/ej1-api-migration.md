---
title: "Migration from Essential JS 1"
component: "RadioButton"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, radio button component."
---

# Migration from Essential JS 1

This article describes the API migration process of RadioButton component from Essential JS 1 to Essential JS 2.

## Properties

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| RadioButton Label | **Property:** *text* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>text: "RadioButton" <br/> });  | **Property:** *label* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>label: "RadioButton" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Checked state | **Property:** *checked* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>checked: true <br/> });  | **Property:** *checked* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>checked: true<br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Adding custom class | **Property:** *cssClass* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>cssClass: "custom-class" <br/> });  | **Property:** *cssClass* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>cssClass: "custom-class" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Disabled state | **Property:** *enabled* <br/><br/>  $("#radiobutton").ejRadioButton({ <br/>enabled: false <br/> });  | **Property:** *disabled* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>disabled: true <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| State persistence | **Property:** *enablePersistence* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>enablePersistence: true <br/> });  | **Property:** *enablePersistence* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>enablePersistence: true <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| RTL | **Property:** *enableRTL* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>enableRTL: true, <br/> text: "RadioButton"<br/> });  | **Property:** *enableRtl* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>enableRtl: true, <br/> label: "RadioButton" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| HTML Attributes | **Property:** *htmlAttributes* <br/><br/>  $("#radiobutton").ejRadioButton({ <br/>htmlAttributes : { required:"required" }, <br/> text: "RadioButton" <br/>});  | Not applicable |
| Id property | **Property:** *id* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>id: "sync" <br/> });  | Not applicable |
| Prefix value of Id | **Property:** *idPrefix* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>idPrefix: "ej" <br/> });  | Not applicable |
| Name attribute | **Property:** *name* <br/><br/> $("#radiobutton").ejRadioButton({ <br/> name: "sports" <br/> });  | **Property:** *name* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/> name: "sports" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Value attribute | **Property:** *value* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>value: "football", <br/>name: "sports" <br/> });  | **Property:** *value* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>value: "football", <br/>name: "sports" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Size | **Property:** *size* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>size: "small" <br/> });  | **Property:** *cssClass* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>cssClass: "e-small" <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Validation rules | **Property:** *validationRules* <br/><br/> $("#radiobutton").ejRadioButton({ <br/> validationRules:{ required:true } <br/> });  | Not applicable |
| Validation message | **Property:** *validationMessage* <br/><br/> $("#radiobutton").ejRadioButton({ <br/> validationRules:{ required:true }, <br/>validationMessage: { required: "Required RadioButton value" } <br/> });  | Not applicable |

## Methods

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Destroy | **Method:** *destroy* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>text: "RadioButton" <br/> }); <br/> var radioButton = $("#radiobutton").data("ejRadioButton"); <br/>radioButton.destroy()  | **Method:** *destroy* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>label: "RadioButton" <br/>}); <br/>radioButton.appendTo("#radiobutton");<br/>radioButton.destroy(); |
| Disable the RadioButton | **Method:** *disable* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>text: "RadioButton" <br/> }); <br/> var radioButton = $("#radiobutton").data("ejRadioButton"); <br/>radiobutton.disable()  | Not applicable |
| Enable the RadioButton | **Method:** *enable* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>text: "RadioButton" <br/> }); <br/> var radioButton = $("#radiobutton").data("ejRadioButton"); <br/>radiobutton.enable()  | Not applicable |

## Events

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| BeforeChange Event | **Events:** *beforeChange* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>beforeChange: function(args) { /** code block */ } <br/> });  | Not applicable |
| Change Event | **Events:** *change* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>change: function(args) { /** code block */ } <br/> });  | **Events:** *change* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>change: function(args) { /** code block */ } <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Create Event | **Events:** *create* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>create: function(args) { /** code block */ } <br/> });  | **Events:** *created* <br/><br/> var radioButton = new ej.buttons.RadioButton({ <br/>created: function() { /** code block */ } <br/>}); <br/>radioButton.appendTo("#radiobutton"); |
| Destroy Event | **Events:** *destroy* <br/><br/> $("#radiobutton").ejRadioButton({ <br/>destroy: function(args) { /** code block */ } <br/> });  | Not applicable |