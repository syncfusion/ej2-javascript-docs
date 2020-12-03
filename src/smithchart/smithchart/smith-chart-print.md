# Print and Export

## Print

The rendered smithchart can be printed directly from the browser by calling the public method print. ID of the smithchart's div element must be passed as argument to that method.

{% tab template= "smithchart/smithchart-print", sourceFiles="index.ts,index.html", es5Template="es5print" %}

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
        }
    ],
});

smithchart.appendTo('#element');

document.getElementById('print').onclick = () => {
    smithchart.print();
};
```

{% endtab %}

## Export

The rendered smithchart can be exported to JPEG , PNG, SVG or PDF format by using export method in smithchart. Input parameters for this method are Export Type for format and fileName of result.

{% tab template= "smithchart/smithchart-print", sourceFiles="index.ts,index.html", es5Template="es5Export" %}

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
        }
    ],
});

smithchart.appendTo('#element');

document.getElementById('print').onclick = () => {
    smithchart.export('PNG', 'result');
};
```

{% endtab %}