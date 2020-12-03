<!-- markdownlint-disable MD036 -->

# Marker & Datalabels

Markers and Datalabels are used to provide information about the data points in the series. You can add a shape to adorn each data point. By default marker and datalabel both are disabled in smithchart. You can enable both of them by setting visible property as true in marker and datalabel settings

## Marker

Default visibility of marker is false. You can enable the marker by setting property visible as true in marker settings. This will add marker for each point in the series. Using marker setting, you can customize marker differently for each series in smithchart.

{% tab template= "smithchart/smithchart-marker", sourceFiles="index.ts,index.html", es5Template="es5marker" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    series: [
        {
            points: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            marker: {
                visible: true
            }
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}

**Marker Customization**

Using marker settings in series, you can customize the marker for each series differently. Using marker settings, you can customize following properties differently for each series in the smithchart.

* [`width`] - To control the width of the marker.
* [`height`] - To control the height of the marker.
* [`fill`] - Used to customize the fill color of the marker.
* [`opacity`] - Used to customize the opacity of the marker.
* [`border`] - Used to control the width and color of the marker's border.
* [`shape`] - Used to change the shape of the marker.

{% tab template= "smithchart/smithchart-marker", sourceFiles="index.ts,index.html", es5Template="es5CustomMarker" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    series: [
        {
            points: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            marker: {
                visible: true,
                height: 10,
                width: 10,
                fill: '#ff99ff',
                opacity: 1,
                shape: 'rectangle',
                border: {
                    color: '#cc00cc',
                    width: 2
                }
            }
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}

## Datalabels

By default, datalabel is disabled. You can enable the datalabel by setting property visible as true in datalabel settings. For each point in series, data label is created. Datalabel for each series can be customized differently using datalabel settings.

{% tab template= "smithchart/smithchart-marker", sourceFiles="index.ts,index.html", es5Template="es5Label" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    series: [
        {
            points: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            marker: {
                dataLabel: {
                    visible: true
                }
            }
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}

**Datalabel customization**

Using datalabel settings in marker, you can customize the datalabel for each series differently. In datalabel, you can customize the following properties differently for each series.

* [`fill`] - Used to changes the fill color of the data label's shape.
* [`opacity`] - Used to control the opacity of the data label's shape.
* [`border`] - Used to customize the width and color of the border.
* [`textStyle`] - Used to customize the font color, width and size.

{% tab template= "smithchart/smithchart-marker", sourceFiles="index.ts,index.html", es5Template="es5CustomLabel" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    series: [
        {
            points: [
                { resistance: 10, reactance: 25 }, { resistance: 8, reactance: 6 },
                { resistance: 6, reactance: 4.5 }, { resistance: 4.5, reactance: 2 },
                { resistance: 3.5, reactance: 1.6 }, { resistance: 2.5, reactance: 1.3 },
                { resistance: 2, reactance: 1.2 }, { resistance: 1.5, reactance: 1 },
                { resistance: 1, reactance: 0.8 }, { resistance: 0.5, reactance: 0.4 },
                { resistance: 0.3, reactance: 0.2 }, { resistance: 0, reactance: 0.15 },
            ],
            name: 'Transmission1',
            marker: {
                dataLabel: {
                    visible: true,
                    fill: '#99ffcc',
                    opacity: 1,
                    border: {
                        color: '#1aff8c',
                        width: 2,
                    }
                }
            }
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}