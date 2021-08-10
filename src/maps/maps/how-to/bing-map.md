# Display geometry shape in bing maps

Usually bing map displays the Maps in satellite view in which you can't make changes as per your requirement. To over come this, you can add maps shape as sublayer over the bing map and you can customize it as per your requirement. Kindly follow the below steps to add geometry shapes as sublayer in bing maps.

**Step 1**:

To render the Maps control as bing map, set the [`layerType`](../api/maps/layerSettingsModel/#layertype) as **Bing** and also provide the key for the bing map.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html" ,es5Template="bing" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';

let map: Maps = new Maps({
    layers: [
        {
            layerType: 'Bing',
            // Provide your bing map key here
            key: 'AuQazZ3PUo3p2_c2KPhqMku-iKvee5fKcRREIg46MENqVTM9dp2ZyTbrHJpR9esZ'
        }
    ]
});

map.appendTo("#container");

```

{% endtab %}

**Step 2**:

The geometry shape can be added in the bing map using sublayer concept. In the below example, Africa continent can be set as the sublayer in bing map using the [`type`](../api/maps/layerSettingsModel/#type) property.

{% tab template="maps/default-map", sourceFiles="index.ts,index.html" ,es5Template="bing-map" %}

```typescript

import { Maps } from '@syncfusion/ej2-maps';
import { Africa_Continent } from './Africa_Continent.ts';

let map: Maps = new Maps({
    layers: [
        {
            layerType: 'Bing',
            key: 'AuQazZ3PUo3p2_c2KPhqMku-iKvee5fKcRREIg46MENqVTM9dp2ZyTbrHJpR9esZ'
        },
        {
            layerType: 'Geometry',
            type: 'SubLayer',
            shapeData: Africa_Continent,
            shapeSettings: {
                fill: 'blue'
            }
        }
    ]
});

map.appendTo("#container");

```

{% endtab %}