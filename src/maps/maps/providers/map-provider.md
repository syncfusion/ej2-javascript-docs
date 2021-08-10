---
title: " Open Street Maps in EJ2 Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Open Street Maps of Syncfusion EJ2 Maps control and more."
---

# Open Street Maps in EJ2 Maps control

The OpenStreetMap (OSM) is the online map provider built by a community of developers; it is free to use under an open license. It allows to view geographical data in a collaborative way from anywhere on the earth. The OSM map provides small tile images based on our requests and combines those images into a single image to display the map area in the Maps component.

## Adding OpenStreetMap

The OSM map can be rendered using by setting the [`layerType`](../api/maps/layerSettingsModel/#layertype) property value as "**OSM**".

{% tab template= "maps/Providers", es5Template="OSM" %}

{% endtab %}

### Changing the tile server of the OpenStreetMap

The OSM tile server can be changed by setting the tile URL in the [`urlTemplate`](../api/maps/layerSettingsModel/#urltemplate) property. For more details about the OSM tile server, refer [here](https://wiki.openstreetmap.org/wiki/Tiles).

## Zooming and panning

The OSM maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a map for in-depth analysis. Panning helps to move a map around to focus the targeted area.

{% tab template= "maps/Providers", es5Template="OSMZoom" %}

{% endtab %}

## Adding markers and navigation line

Markers can be added to the layers of OSM maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings) property. Navigation lines can be added on top of an OSM maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings) property.

{% tab template= "maps/Providers", es5Template="OSMMarkers" %}

{% endtab %}

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the OSM maps layer for highlighting a particular continent or country in OSM maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of maps layer to "**SubLayer**".

{% tab template= "maps/default-map", es5Template="OSMSublayer" %}

{% endtab %}