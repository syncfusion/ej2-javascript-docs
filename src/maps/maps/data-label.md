---
title: "Data Labels in EJ2 Maps control | Syncfusion"

component: "Maps"

description: "Learn here all about Data Labels of Syncfusion EJ2 Maps control and more."
---

# Data labels in EJ2 Maps control

Data labels provide information to users about the shapes of the Maps control. It can be enabled by setting the [`visible`](../api/maps/dataLabelSettingsModel/#visible) property of the [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) to **true**.

## Adding data labels

To display data labels in the Maps, the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) of [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) must be used. The value of the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property can be taken from the field name in the shape data or data source. In the following example, the value of the [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property is the field name in the shape data of the Maps layer.

{% tab template="maps/default-map", es5Template="dataLabel" %}

{% endtab %}

In the following example, the value of [`labelPath`](../api/maps/dataLabelSettingsModel/#labelpath) property is set from the field name in the data source of the layer settings.

{% tab template="maps/default-map", es5Template="label-datasource" %}

{% endtab %}

## Customization

The following properties are available in the [`dataLabelSettings`](../api/maps/dataLabelSettingsModel/) to customize the data label of the Maps control.

* [`border`](../api/maps/dataLabelSettingsModel/#border) - To customize the color, width and opacity for the border of the data labels in Maps.
* [`fill`](../api/maps/dataLabelSettingsModel/#fill) - To apply the color of the data labels in Maps.
* [`opacity`](../api/maps/dataLabelSettingsModel/#opacity) - To customize the transparency of the data labels in Maps.
* [`textStyle`](../api/maps/dataLabelSettingsModel/#textstyle) - To customize the text style of the data labels in Maps.

{% tab template="maps/default-map", es5Template="labelCustomization" %}

{% endtab %}

## Smart labels

The Maps control provides an option to handle the labels when they intersect with the corresponding shape borders using the [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) property. The following options are available in the [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) property.

* None
* Hide
* Trim

{% tab template="maps/default-map", es5Template="labelSmartMode" %}

{% endtab %}

## Intersect action

The Maps component provides an option to handle the labels when a label intersects with another label using the [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) property. The following options are available in the [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) property.

* None
* Hide
* Trim

{% tab template="maps/default-map", es5Template="labelIntersect" %}

{% endtab %}

## Adding data label as a template

The data label can be added as a template in the Maps component. The [`template`](../api/maps/dataLabelSettingsModel/#template) property of [`dataLabelSettings`](../api/maps/dataLabelSettingsModel) is used to set the data label as a template. Any text or HTML element can be added as the template in data labels.

>The customization properties of data label, [`smartLabelMode`](../api/maps/dataLabelSettingsModel/#smartlabelmode) and [`intersectionAction`](../api/maps/dataLabelSettingsModel/#intersectionaction) properties are not applicable to [`template`](../api/maps/dataLabelSettingsModel/#template) property. The styles can be applied to the label template using the CSS styles of the template element.

{% tab template="maps/default-map", es5Template="labelTemplate" %}

{% endtab %}