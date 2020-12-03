# Working with Data

Smithchart can visualise the data bound from local data. The data you bind for the smithchart, should be an array of object and that should contain the field resistance and rectangle. This should be bind to points or datasource in the smithchart.

## Data Binding

You can bind simple JSON data to smithchart using point property in series. JSON data should contain [`resistance`] and [`reactance`] fields. This JSON data should be bind to points or datasource in the smithchart. You can any number of JSON for points or datasource as per your requirement.

{% tab template= "smithchart/working-with-data", sourceFiles="index.ts,index.html", es5Template="es5data" %}

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
        }, {
            points: [
                { resistance: 20, reactance: -50 }, { resistance: 10, reactance: -10 },
                { resistance: 9, reactance: -4.5 }, { resistance: 8, reactance: -3.5 },
                { resistance: 7, reactance: -2.5 }, { resistance: 6, reactance: -1.5 },
                { resistance: 5, reactance: -1 }, { resistance: 4.5, reactance: -0.5 },
                { resistance: 3.5, reactance: 0 }, { resistance: 2.5, reactance: 0.4 },
                { resistance: 2, reactance: 0.5 }, { resistance: 1.5, reactance: 0.5 },
                { resistance: 1, reactance: 0.4 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0, reactance: 0.05 },
            ],
        },
    ],
});

smithchart.appendTo('#container');
```

{% endtab %}