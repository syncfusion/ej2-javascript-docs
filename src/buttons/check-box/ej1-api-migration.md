---
title: "Migration from Essential JS 1"
component: "CheckBox"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, checkbox component."
---

# Migration from Essential JS 1

This article describes the API migration process of Checkbox component from Essential JS 1 to Essential JS 2.

## Properties

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Checkbox Label | **Property:** *text* <br/><br/> $("#checkbox").ejCheckBox({ <br/>text: "Checkbox" <br/> });  | **Property:** *label* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>label: "Checkbox" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Checked state | **Property:** *checked* <br/><br/> $("#checkbox").ejCheckBox({ <br/>checked: true <br/> });  | **Property:** *checked* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/> checked: true <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Indeterminate state | **Property:** *enableTriState and checkState* <br/><br/> $("#checkbox").ejCheckBox({ <br/>enableTriState: true, <br/>checkState: "indeterminate" <br/> });  | **Property:** *indeterminate* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>indeterminate: true<br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Adding custom class | **Property:** *cssClass* <br/><br/> $("#checkbox").ejCheckBox({ <br/>cssClass: "custom-class" <br/> });  | **Property:** *cssClass* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>cssClass: "custom-class" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Disabled state | **Property:** *enabled* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>enabled: false <br/> });  | **Property:** *disabled* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>disabled: true <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| State persistence | **Property:** *enablePersistence* <br/><br/> $("#checkbox").ejCheckBox({ <br/>enablePersistence: true <br/> });  | **Property:** *enablePersistence* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>enablePersistence: true <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| RTL | **Property:** *enableRTL* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>enableRTL: true, <br/> text: "Checkbox"<br/> });  | **Property:** *enableRtl* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>enableRtl: true, <br/> label: "Checkbox" }); <br/>checkbox.appendTo("#checkbox"); |
| HTML Attributes | **Property:** *htmlAttributes* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>htmlAttributes : { required:"required" }, <br/> text: "Checkbox" <br/>});  | Not applicable |
| Id property | **Property:** *id* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>id: "sync" <br/> });  | Not applicable |
| Prefix value of Id | **Property:** *idPrefix* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>idPrefix: "ej" <br/> });  | Not applicable |
| Name attribute | **Property:** *name* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>name: "sports" <br/> });  | **Property:** *name* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>name: "sports" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Value attribute | **Property:** *value* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>value: "football", <br/>name: "sports" <br/> });  | **Property:** *value* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>value: "football", <br/>name: "sports" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Show rounded corner | **Property:** *showRoundedCorner* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>showRoundedCorner: true <br/> });  | Not applicable |
| Size | **Property:** *size* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>size: "small" <br/> });  | **Property:** *cssClass* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>cssClass: "e-small" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Label position | Not applicable | **Property:** *labelPosition* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>label: "Checkbox", <br/>labelPosition: "Before" <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Validation rules | **Property:** *validationRules* <br/><br/>  $("#checkbox").ejCheckBox({ <br/> validationRules:{ required:true } <br/> });  | Not applicable |
| Validation message | **Property:** *validationMessage* <br/><br/>  $("#checkbox").ejCheckBox({ <br/> validationRules:{ required:true }, <br/>validationMessage: { required: "Required CheckBox value" } <br/> });  | Not applicable |

## Methods

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| Destroy | **Method:** *destroy* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>text: "Checkbox" <br/> }); <br/> var checkbox = $("#checkbox").data("ejCheckBox"); <br/>checkbox.destroy(); | **Method:** *destroy* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/>label: "Checkbox" <br/>}); <br/>checkbox.appendTo("#checkbox");<br/>checkbox.destroy(); |
| Disable the Checkbox | **Method:** *disable* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>text: "Checkbox" <br/> }); <br/> var checkbox = $("#checkbox").data("ejCheckBox"); <br/>checkbox.disable(); | Not applicable |
| Enable the Checkbox | **Method:** *enable* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>text: "Checkbox" <br/> }); <br/> var checkbox = $("#checkbox").data("ejCheckBox"); <br/>checkbox.enable(); | Not applicable |
| Check state of the Checkbox | **Method:** *isChecked* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>text: "Checkbox" <br/> }); <br/> var checkbox = $("#checkbox").data("ejCheckBox"); <br/>checkbox.isChecked(); | Not applicable |

## Events

| Behavior | API in Essential JS 1 | API in Essential JS 2 |
| --- | --- | --- |
| BeforeChange Event | **Events:** *beforeChange* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>beforeChange: function (args) { /** code block */ } <br/> });  | Not applicable |
| Change Event | **Events:** *change* <br/><br/>  $("#checkbox").ejCheckBox({ <br/> change: function change(args) { /** code block */ } <br/> });  | **Events:** *change* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/> change: function change(args) { /** code block */ } <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Create Event | **Events:** *create* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>create: function(args) { /** code block */ } <br/> });  | **Events:** *created* <br/><br/> var checkbox= new ej.buttons.CheckBox({ <br/> created: function created() { /** code block */ } <br/>}); <br/>checkbox.appendTo("#checkbox"); |
| Destroy Event | **Events:** *destroy* <br/><br/>  $("#checkbox").ejCheckBox({ <br/>destroy: function (args) { /** code block */ } <br/> }); | Not applicable |