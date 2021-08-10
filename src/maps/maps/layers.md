# Layers

The Maps component is rendered through [`layers`](../api/maps/#layers) and any number of layers can be added to the Maps.

## Multilayer

The Multilayer support allows loading multiple shapefiles and map providers in a single container, enabling Maps to display more information. The shape layer or map providers are the main layers of the Maps. Multiple layers can be added as **SubLayer** over the main layers using the [`type`](../api/maps/layerSettingsModel/#type) property in the [`layers`](../api/maps/layerSettingsModel/#type) property.

## SubLayer

Sublayer is a type of shape file layer. It allows loading multiple shape files in a single map view. For example, a sublayer can be added over the main layer to view geographic features such as rivers, valleys and cities in a map of a country. Similar to the main layer, elements in the Maps such as markers, bubbles, color mapping and legends can be added to the sub-layer.

In this example, the United States map shape is used as shape data by utilizing the **usa.ts** file, and the **texas.ts** and **california.ts** files are used as sub-layers in the United States map.

{% tab template= "maps/default-map", es5Template="layers" %}

{% endtab %}

## Displaying layer in the view

Multiple shape files and map providers can be loaded simultaneously in Maps. The [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) property is used to determine which layer on the user interface should be displayed. This property is used for the Maps drill-down feature, so when the [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value is changed, the corresponding shape is loaded. In this example, two layers can be loaded with the World map and the United States map. Based on the given [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value the corresponding shape will be loaded in the user interface. If the [`baseLayerIndex`](../api/maps/mapsModel/#baselayerindex) value is set to 0, then the world map will be loaded.

{% tab template= "maps/default-map", es5Template="layerView" %}

{% endtab %}

## See Also

* [Adding multiple layers in map](../maps/how-to/multiple-layer)
* [Display geometry shape in bing maps](../maps/how-to/bing-map)
* [Custom path map](../maps/how-to/custom-path)