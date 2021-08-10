---
title: " Bing Maps in EJ2 Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Bing Maps of Syncfusion EJ2 Maps control and more."
---

# Bing Maps in EJ2 Maps control

Bing maps is a online map provider owned by Microsoft. As like OSM, it provides map tile images based on our requests and combines those images into a single one to display the map area.

## Adding Bing Maps

The Bing Maps can be rendered by setting the [`layerType`](../api/maps/layerSettingsModel/#layertype) property as "**Bing**" and the key for the Bing Maps must be set in the [`key`](../api/maps/layerSettingsModel/#key) property. The Bing Maps key can be obtained from [here](https://www.microsoft.com/en-us/maps/create-a-bing-maps-key).

```typescript
var map = new ej.maps.Maps({
    layers: [{
        layerType: 'Bing',
        bingMapType: 'AerialWithLabel',
        key: ''    // Add Bing map key here
    }]
});
map.appendTo('container');
```

> Specify Bing map key in the `key` property.

## Types of Bing maps

Bing Maps provides different types of maps and it is supported in the Maps control.

* **Aerial** - Displays satellite images to highlight roads and major landmarks for easy identification.
* **AerialWithLabel** - Displays aerial map with labels for the continent, country, ocean, etc.
* **Road** - Displays the default map view of roads, buildings, and geography.
* **CanvasDark** - Displays dark version of the road maps.
* **CanvasLight** - Displays light version of the road maps.
* **CanvasGray** - Displays grayscale version of the road maps.

To render the light version of the road maps, set the `bingMapType` to `CanvasLight` as demonstrated in the following code sample.

```typescript
var map = new ej.maps.Maps({
    zoomSettings: {
        zoomFactor: 12,
    },
    centerPosition : {
        latitude: 38.8951,
        longitude: -77.0364
    },
    layers: [{
        layerType: 'Bing',
        bingMapType: 'CanvasLight',
        key: ''    // Add Bing map key here
    }]
});
map.appendTo('container');
```

> Specify Bing maps key in the `key` property.

## Zooming and panning

Bing maps layer can be zoomed and panned. Zooming helps to get a closer look at a particular area on a map for in-depth analysis. Panning helps to move a map around to focus the targeted area.

```typescript
var map = new ej.maps.Maps({
    zoomSettings: {
        enable: true,
        toolBars: [{ "Zoom", "ZoomIn", "ZoomOut", "Pan", "Reset" }]
    },
    layers: [{
        layerType: 'Bing',
        key: ''    // Add Bing map key here
    }]
});
map.appendTo('container');
```

> Specify Bing map key in the `key` property.

## Adding markers and navigation line

Markers can be added to the layers of Bing maps by setting the corresponding location's coordinates of latitude and longitude using [`markerSettings`](../api/maps/layerSettingsModel/#markersettings) property. Navigation lines can be added on top of an Bing maps layer for highlighting a path among various places by setting the corresponding location's coordinates of latitude and longitude in the [`navigationLineSettings`](../api/maps/layerSettingsModel/#navigationlinesettings) property.

```typescript
var map = new ej.maps.Maps({
    zoomSettings: {
        zoomFactor: 4
    },
    centerPosition: {
        latitude: 29.394708
        logitude: -94.954653
    },
    layers: [{
        layerType: 'Bing',
        bingMapType: 'CanvasLight',
        key: '',    // Add Bing map key here
        markerSettings: [{
            visible: true,
            height: 25,
            width: 15,
            dataSouce: [{
                latitude: 34.060620,
                longitude: -118.330491,
                name: "California"
            },
            {
                latitude: 40.724546,
                longitude: -73.850344,
                name: "New York"
            }],
        }],
        navigationLineSettings: [{
            visible: true,
            color: "blue",
            angle: 0.1,
            latitude: {
                34.060620, 40.724546
            },
            longitude: {
                -118.330491, -73.850344
            }
        }]
    }]
});
map.appendTo('container');
```

> Specify Bing map key in the `Key` property.

## Sublayer

Any GeoJSON shape can be rendered as a sublayer on top of the Bing maps layer for highlighting a particular continent or country in Bing maps by adding another layer and specifying the [`type`](../api/maps/layerSettingsModel/#type) property of maps layer to "**SubLayer**".
