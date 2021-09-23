---
title: " Internationalization in EJ2 Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Internationalization of Syncfusion EJ2 Maps control and more."
---

# Internationalization

Maps provide support for internationalization for the below elements.

* Data label
* Tooltip

For more information about number and date formatter, refer to the
[`internationalization`](http://ej2.syncfusion.com/documentation/base/intl.html) section.

<!-- markdownlint-disable MD036 -->

## Globalization

Globalization is the process of designing and developing a component that works in different
cultures/locales. Internationalization library is used to globalize number, date, time values in
Maps component using [`format`](../api/maps/mapsModel/#format) property in the [`Maps`](../api/maps/mapsModel).

## Numeric Format

The numeric formats such as currency, percentage and so on can be displayed in the tooltip and data labels of the Maps using the [`format`](../api/maps/mapsModel/#format) property in the [`Maps`](../api/maps/mapsModel). In the below example, the tooltip is globalized to **German** culture. When setting the [`useGroupingSeparator`](../api/maps/mapsModel/#usegroupingseparator) property as **true**, the numeric text in the Maps separates with the comma separator.

```typescript
import { Maps, MapsTooltip } from '@syncfusion/ej2-maps';
import { world_map } from './world-map.ts';
import { setCulture } from '@syncfusion/ej2-base';
setCulture('de');
Maps.Inject(MapsTooltip);
let maps: Maps = new Maps({
    format: 'c',
    useGroupingSeparator: true,
    layers: [
        {
            shapeData: world_map,
            dataSource: [
                { "Country": "China", "Membership": "Permanent", population: '38332521' },
                { "Country": "France", "Membership": "Permanent", population: '19651127' },
                { "Country": "Russia", "Membership": "Permanent", population: '3090416' },
                { "Country": "Kazakhstan", "Membership": "Non-Permanent", population: '1232521' },
                { "Country": "Poland", "Membership": "Non-Permanent", population: '90332521' },
                { "Country": "Sweden", "Membership": "Non-Permanent", population: '383521' }
            ],
            shapePropertyPath: 'name',
            shapeDataPath: 'Country',
            shapeSettings: {
                colorValuePath: 'Membership',
                colorMapping: [
                {
                    value: 'Permanent', color: '#D84444'
                },
                {
                    value: 'Non-Permanent', color: '#316DB5'
                }]
            },
            tooltipSettings: {
                visible: true,
                valuePath: 'population'
            }
        }
    ]
});
maps.appendTo('#element');
```