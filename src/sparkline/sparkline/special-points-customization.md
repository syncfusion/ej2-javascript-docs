# Special points customization

You can customize the points by initializing the point colors. The customization options allows to differentiate the [`start`], [`end`], [`positive`], [`negative`], and [`low`] points. This customization is only applicable for line, column, and area type sparklines.

<!-- markdownlint-disable MD036 -->

{% tab template= "sparkline/specialpoint-customization", sourceFiles="index.ts,index.html" , es5Template="es5SpecialPoint" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
 height: '150px',
    width: '130px',
    dataSource: [
            { x: 0, xval: 'AUDI', yval: 1 },
            { x: 1, xval: 'BMW', yval: 5 },
            { x: 2, xval: 'BUICK', yval: -1 },
            { x: 3, xval: 'CETROEN', yval: -6 },
            { x: 4, xval: 'CHEVROLET', yval: 0 },
            { x: 5, xval: 'FIAT', yval: 1 },
            { x: 6, xval: 'FORD', yval: -2 },
            { x: 7, xval: 'HONDA', yval: 7 },
            { x: 8, xval: 'HYUNDAI', yval: -9 },
            { x: 9, xval: 'JEEP', yval: 0 },
            { x: 10, xval: 'KIA', yval: -10 },
            { x: 11, xval: 'MAZDA', yval: 3 }
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'Column' as type of the sparkline
    type:'Column',
    // Assign "Category" as the value type of the sparkline
    valueType: 'Category',
    // To configure sparkline series highest y value point color.
    highPointColor:'blue',
    // To configure sparkline series lowest y value point color.
    lowPointColor:'orange',
    // To configure sparkline series first x value point color.
    startPointColor:'green',
    // To configure sparkline series last x value point color.
    endPointColor:'green',
    // To configure sparkline series negative y value point color.
    negativePointColor:'red'
}, '#element');
```

{% endtab %}

**Tie point color**

Tie point color is used to configure the win-loss series type sparkline's y-value point color. The following code sample shows the tie point color of sparkline series.

{% tab template= "sparkline/specialpoint-customization", sourceFiles="index.ts,index.html" , es5Template="es5TiePoint" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
   height: '150px',
    width: '130px',
    dataSource: [12, 15, -10, 13, 15, 6, -12, 17, 13, 0, 8, -10],
    // Assign the 'WinLoss' as type of Sparkline
    type:'WinLoss',
    // Assign "Numeric" as the value type of the sparkline
    valueType: 'Numeric',
    tiePointColor:'blue'
}, '#element');
```

{% endtab %}
