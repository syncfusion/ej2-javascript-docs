# Title and Subtitle

## Enable title

Title and subtitle is used to depicts the information about the data plotted in the smithchart. You can set the title and subtitle of the smithchart using the [`text`] property in title and subtitle. By default visibility of the title as well as subtitle is enabled. You need to set simply text for title and subtitle in your sample as like below.

{% tab template= "smithchart/title-subtitle", sourceFiles="index.ts,index.html", es5Template="es5title" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    title : {
        text: 'Impedance Transmission',
        subtitle: {
            text: 'Transmission'
        }
    },
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
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}

## Title trim

Both title and subtitle of the smithchart can be trimmed if it exceeds the certain length. Trimming is enabled using [`enableTrim`] for title as well as subtitle. This length can be changed using the property [`maximumWidth`]. Also [`font`], [`textAlignment`] and [`visibility`] can be customized for title as well as subtitle.

{% tab template= "smithchart/title-subtitle", sourceFiles="index.ts,index.html", es5Template="es5TitleTrim" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    title : {
        enableTrim: true,
        maximumWidth: 70,
        textAlignment: 'Center',
        visible: true,
        text: 'Impedance Transmission',
        subtitle: {
            text: 'Transmission',
            visible: true,
            textAlignment: 'Far',
            enableTrim: true,
            maximumWidth: 40
        }
    },
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
        }
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}