# Multilayer

The multilayer support allows loading multiple shape files in a single container and enables Maps to display more information. The shape layer is the main layer of the Maps. Multiple layers can be added in a shape layer as **SubLayer** using the [`type`](../api/maps/type/) property.

{% tab template= "maps/default-map", sourceFiles="index.ts,index.html" , es5Template="layers" %}

```typescript
import { usa_map } from './usa.ts';
import { california } from './california.ts';
import { texas } from './texas.ts';
import { Maps } from '@syncfusion/ej2-maps';

// initialize Maps component
let map: Maps = new Maps({
    layers: [
        {
            shapeData: usa_map,
            shapeSettings: {
                fill: '#E5E5E5',
                border: {
                    color: 'black',
                    width: 0.1
                }
            }
        },
        {
            shapeData: texas,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        },
        {
            shapeData: california,
            type: 'SubLayer',
            shapeSettings: {
                fill: 'rgba(141, 206, 255, 0.6)',
                border: {
                    color: '#1a9cff',
                    width: 0.25
                }
            }
        }
    ]
}, '#element');
```

{% endtab %}
