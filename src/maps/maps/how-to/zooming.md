# Center position zooming

The center position zooming can be achieved by using the [`centerPosition`](../api/maps#centerposition) and [`zoomFactor`](../api/maps/zoomSettingsModel/#zoomfactor) properties as mentioned in the following example. The center position is used to configure the zoom level of Maps, and the zoom factor is used to specify the center position where the Maps should be displayed.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="position" %}

```typescript
import { world_map } from './world-map.ts';
import { Maps,Zoom, ZoomSettings } from '@syncfusion/ej2-maps';
Maps.Inject(Zoom);

// initialize Maps component
let map: Maps = new Maps({
    zoomSettings:{
    enable: true,
    zoomFactor:13
    },
    centerPosition: {
        latitude: 25.54244147012483,
        longitude: -89.62646484375
    },
       layers: [
        {
            shapeData: world_map
        }
    ]
}, '#element');
```

{% endtab %}