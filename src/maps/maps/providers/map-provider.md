---
title: "Open Street Maps in EJ2 Maps control | Syncfusion"

component: "Maps"

description: "Learn here all about Open Street Maps of Syncfusion EJ2 Maps control and more."
---

# OpenStreetMaps in EJ2 Maps control

The OpenStreetMap (OSM) is the online Maps provider built by a community of developers; it is free to use under an open license. It allows to view geographical data in a collaborative way from anywhere on the earth. The OSM Maps provides small tile images based on our requests and combines those images into a single image to display the Maps area in the Maps component.

## Adding OpenStreetMap

The OSM Maps can be rendered using by setting the [`layerType`](../api/maps/layerSettingsModel/#layertype) property value as **OSM**.

{% tab template= "maps/Providers", es5Template="OSM" %}

{% endtab %}

### Changing the tile server of the OpenStreetMap

The OSM tile server can be changed by setting the tile URL in the [`urlTemplate`](../api/maps/layerSettingsModel/#urltemplate) property. For more details about the OSM tile server, refer [here](https://wiki.openstreetmap.org/wiki/Tiles).

## Zooming and Panning

The OSM Maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a Maps for in-depth analysis. Panning helps to move a Maps around to focus the targeted area.

{% tab template= "maps/Providers", es5Template="OSMZoom" %}

{% endtab %}

## Adding markers and navigation line

Markers can be added to the layers of OSM Maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings). Navigation lines can be added on top of an OSM Maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings).

{% tab template= "maps/Providers", es5Template="OSMMarkers" %}

{% endtab %}

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the OSM Maps layer for highlighting a particular continent or country in OSM Maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of Maps layer to **SubLayer**.

{% tab template= "maps/default-map", es5Template="OSMSublayer" %}

{% endtab %}