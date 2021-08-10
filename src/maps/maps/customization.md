---
title: " Customization in EJ2 Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Customization of Syncfusion EJ2 Maps control and more."
---

# Customization in EJ2 Maps control

## Setting the size for Maps

The width and height of the Maps can be set using the [`width`](../api/maps/mapsModel/#width) and [`height`](../api/maps/mapsModel/#height) properties in the Maps control. Percentage or pixel values can be used for the height and width values.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="map-size" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    height: '200px',
    width: '500px',
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Maps title

The title for the Maps can be set using the [`titleSettings`](../api/maps/titleSettingsModel) property. It can be customized using the following properties.

* [`alignment`](../api/maps/titleSettingsModel/#alignment) - To customize the alignment for the text in the title for the Maps. The possible values are "**Center**", "**Near**" and "**Far**".
* [`description`](../api/maps/titleSettingsModel/#description) - To set the description of the title in Maps.
* [`text`](../api/maps/titleSettingsModel/#text) - To set the text for the title in Maps.
* [`textStyle`](../api/maps/titleSettingsModel/#textstyle) - To customize the text of the title in Maps.
* [`subtitleSettings`](../api/maps/titleSettingsModel/#subtitlesettings) - To customize the subtitle for the Maps.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="map-title" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    titleSettings: {
        text: 'Maps Control',
        textStyle: {
            color: 'red',
            fontStyle: 'italic',
            fontWeight: 'regular',
            fontFamily: 'arial',
            size: '14px'
        },
        alignment: 'Center'
    },
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true,
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Setting theme

The Maps control supports following themes.

* Material
* Fabric
* Bootstrap
* Highcontrast
* MaterialDark
* FabricDark
* BootstrapDark
* Bootstrap4
* HighContrastLight
* Tailwind

By default, the Maps are rendered by the **"Material"** theme. The theme of the Maps component is changed using the [`theme`](../api/maps/#theme) property.

{% tab template="maps/map-theme", sourceFiles="index.ts,index.html",es5Template="theme" %}

```typescript
import { Maps, MapsTheme } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true
        }
    }]
});

map.appendTo('#element');
document.getElementById('theme').onchange = () => {
    var value = (<HTMLInputElement>document.getElementById('theme')).value;
    map.theme= <MapsTheme>value;
    map.refresh();
}
```

{% endtab %}

## Customizing Maps container

The following properties are available to customize the container in the Maps.

* [`background`](../api/maps/mapsModel/#background) - To apply the background color to the container in the Maps.
* [`border`](../api/maps/mapsModel/#border) - To customize the color, width and opacity of the border of the Maps.
* [`margin`](../api/maps/mapsModel/#margin) - To customize the margins of the Maps.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="map-container" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    background: '#CCD1D1',
    border: {
        color: 'green',
        width: 2
    },
    margin: {
        bottom: 10,
        left: 20,
        right: 20,
        top: 10
    },
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Customizing Maps area

By default, the background color of the shape maps is set as white. To modify the background color of the Maps area, the [`background`](../api/maps/mapsAreaSettingsModel/#background) property in the [`mapsArea`](../api/maps/mapsAreaSettingsModel) is used. The border of the Maps area can be customized using the [`border`](../api/maps/mapsAreaSettingsModel/#border) property in the [`mapsArea`](../api/maps/mapsAreaSettingsModel) property.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="map-area" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    mapsArea: {
        background: '#CCD1D1',
        border: {
            width: 2,
            color: 'green'
        }
    },
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Customizing the shapes

The following properties are available in [`shapeSettings`](../api/maps/shapeSettingsModel) property to customize the shapes of the Maps component.

* [`fill`](../api/maps/shapeSettingsModel/#fill) - To apply the color to the shapes.
* [`autofill`](../api/maps/shapeSettingsModel/#autofill) - To apply the palette colors to the shapes if it is set as true.
* [`palette`](../api/maps/shapeSettingsModel/#palette) - To set the custom palette for the shapes.
* [`border`](../api/maps/shapeSettingsModel/#border) - To customize the color, width and opacity of the border of the shapes.
* [`dashArray`](../api/maps/shapeSettingsModel/#dasharray) - To define the pattern of dashes and gaps that is applied to the outline of the shapes.
* [`opacity`](../api/maps/shapeSettingsModel/#opacity) - To customize the transparency for the shapes.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html", es5Template="shape-customization" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapeSettings: {
            autofill: true,
            palette: ['#33CCFF', '#FF0000', '#800000', '#FFFF00', '#808000'],
            border: {
                color: 'green',
                width: 2
            },
            dashArray: '1',
            opacity: 0.9
        }
    }]
});

map.appendTo('#element');
```

## Setting color to the shapes from the data source

The color for each shape in the Maps can be set using the [`colorValuePath`](../api/maps/shapeSettingsModel/#colorvaluepath) property of [`shapeSettings`](../api/maps/shapeSettingsModel) property. The value for the [`colorValuePath`](../api/maps/shapeSettingsModel/#colorvaluepath) property is the field name from the data source of the [`shapeSettings`](../api/maps/shapeSettingsModel) property which contains the color values.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="shape-color" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapePropertyPath: 'continent',
        shapeDataPath: 'continent',
        dataSource: [
            { continent: "North America", color: '#71B081' },
            { continent: "South America", color: '#5A9A77' },
            { continent: "Africa", color: '#498770' },
            { continent: "Europe", color: '#39776C' },
            { continent: "Asia", color: '#266665' },
            { continent: "Oceania", color: '#124F5E' }
        ],
        shapeSettings: {
            colorValuePath: 'color'
        }
    }]
});

map.appendTo('#element');
```

## Applying border to individual shapes

The border of each shape in the Maps can be customized using the [`borderColorValuePath`](../api/maps/shapeSettingsModel/#bordercolorvaluepath) and [`borderWidthValuePath`](../api/maps/shapeSettingsModel/#borderwidthvaluepath) properties to modify the color and the width of the border respectively. The field name in the data source of the layer which contains the color and the width values must be set in the [`borderColorValuePath`](../api/maps/shapeSettingsModel/#bordercolorvaluepath) and [`borderWidthValuePath`](../api/maps/shapeSettingsModel/#borderwidthvaluepath) properties respectively. If the values of [`borderWidthValuePath`](../api/maps/shapeSettingsModel/#borderwidthvaluepath) and [`borderColorValuePath`](../api/maps/shapeSettingsModel/#bordercolorvaluepath) do not match with the field name from the data source, then the color and width of the border will be applied to the shapes using the [`border`](../api/maps/shapeSettingsModel/#border) property in the [`shapeSettings`](../api/maps/shapeSettingsModel) property.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html",es5Template="shape-border" %}

```typescript
import { Maps } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';

let map: Maps = new Maps({
    layers: [{
        shapeData: world_map,
        shapePropertyPath: 'continent',
        shapeDataPath: 'continent',
        dataSource: [
            { continent: "North America", color: '#71B081', borderColor: '#CCFFE5', width: 2 },
            { continent: "South America", color: '#5A9A77', borderColor: 'red', width: 2 },
            { continent: "Africa", color: '#498770', borderColor: '#FFCC99', width: 2 },
            { continent: "Europe", color: '#39776C', borderColor: '#66B2FF', width: 2 },
            { continent: "Asia", color: '#266665', borderColor: '#999900', width: 2 },
            { continent: "Oceania", color: '#124F5E', borderColor: 'blue', width: 2 }
        ],
        shapeSettings: {
            borderColorValuePath: 'borderColor',
            borderWidthValuePath: 'width',
            colorValuePath: 'color'
        }
    }]
});

map.appendTo('#element');
```

{% endtab %}

## Projection type

The Maps control supports the following projection types:

* Mercator
* Equirectangular
* Miller
* Eckert3
* Eckert5
* Eckert6
* Winkel3
* AitOff

By default, the Maps are rendered by the "**Mercator**" projection type in which the Maps are rendered based on the coordinates. So, the Maps is not stretched. To change the type of projection in the Maps, the [`projectionType`](../api/maps/projectionType/) property is used.

{% tab template="maps/projection", sourceFiles="index.ts,index.html" , es5Template="projection" %}

```typescript
import { Maps, ProjectionType } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { projectionData } from './projection-data.ts';

let map: Maps = new Maps({
    projectionType: 'Mercator',
    layers: [{
        shapeData: world_map,
        shapeDataPath: 'Country',
        shapePropertyPath: 'name',
        dataSource: projectionData,
        tooltipSettings: {
            visible: true,
            valuePath: 'Country'
        },
        shapeSettings: {
            fill: '#E5E5E5',
            colorMapping: [
                {
                    value: 'Permanent',
                    color: '#EDB46F'
                },
                {
                    color: '#F1931B',
                    value: 'Non-Permanent'
                }
            ],
            colorValuePath: 'Membership'
        }
    }]
});

map.appendTo('#container');
document.getElementById('projectiontype').onchange = function(){
    let ele: HTMLSelectElement = (<HTMLSelectElement>document.getElementById('projectiontype'))
    maps.projectionType = <ProjectionType>ele.value;
    maps.refresh();
}
```

{% endtab %}
