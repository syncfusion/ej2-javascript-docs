# Marker types

## Add different types of markers

Different marker objects can be added to the Maps component using the marker settings. To update different marker settings in Maps, please follow the given steps:
<!-- markdownlint-disable MD034 -->
**Step 1**:

Initialize the Maps control with marker settings. Here, a marker has been added with specified latitude and longitude of California by using the [`dataSource`](../api/maps/markerSettingsModel/#datasource) property. To customize the shape of the marker using the [`shape`](../api/maps/markerSettingsModel/#shape) property and change the border color and width of the marker using the [`border`](../api/maps/markerSettingsModel/#border) property as mentioned in the following example.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="step-one" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps , Marker, MarkerSettings } from '@syncfusion/ej2-maps';

// Initialize Map component.
let map: Maps = new Maps({
    // Initializing Map with Marker settings.
    layers: [
        {
            shapeData: world_map,
            markerSettings: [
                {
                    dataSource: [
                       { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
                    ],
                    visible:true,
                    shape:'Circle',
                    fill:'white',
                    width:3,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                }
            ]
        }
    ]
});
map.appendTo('#element');  // render initialized Map.
```

{% endtab %}

**Step 2**:

Customize the above option for n number of markers as mentioned in the following example.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template = "step-two" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps , Marker, MarkerSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Marker);
// initialize Maps component
let map: Maps = new Maps({
    layers: [
        {
            shapeData: world_map,
            markerSettings: [
                {
                    dataSource: [
                       { latitude: 37.6276571, longitude: -122.4276688, city: 'San Bruno' },
                    ],
                    visible:true,
                    shape:'Circle',
                    fill:'white',
                    width:3,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                },
                {
                    dataSource: [
                        { latitude: 33.5302186, longitude: -117.7418381, city: 'Laguna Niguel' },
                    ],
                    visible:true,
                    shape:'Rectangle',
                    fill:'yellow',
                    width:15,
                    height:4,
                    animationDuration:0,
                    border:{width:2,color:'#333'}
                },
                {
                    dataSource: [
                         { latitude: 40.7424509, longitude: -74.0081468, city: 'New York' }
                    ],
                    visible:true,
                    shape:'Diamond',
                    fill:'white',
                    width:10,
                    height:10,
                    animationDuration:0,
                    border:{width:2,color:'blue'}
                }
            ]
        }
    ]
});
map.appendTo('#element'); // render initialized Map.
```

{% endtab %}