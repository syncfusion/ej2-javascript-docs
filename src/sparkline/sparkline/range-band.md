# Range Band

This section explains how to customize the sparkline with multiple range bands.

## Range band customization

The range band feature is used to highlight a particular range along with the y-axis using the [`startRange`] and [`endRange`] properties. You can also customize the [`color`] and [`opacity`] of the range band.

{% tab template= "sparkline/range-band", sourceFiles="index.ts,index.html" , es5Template="es5RangeBand" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '150px',
    width: '150px',
    lineWidth: 2,
    fill: '#0d3c9b',
    dataSource:   [0, 6, 4, 1, 3, 2, 5],
    // To configure range band settings
    rangeBandSettings: [
            {
                startRange: 1,
                endRange: 3,
                color: '#bfd4fc',
                opacity:0.4
            }
    ]
}, '#element');
```

{% endtab %}

## Multiple range band customization

You can define multiple range bands to a sparkline as shown in the following code sample.

{% tab template= "sparkline/range-band", sourceFiles="index.ts,index.html" , es5Template="es5MultipleRangeBand" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
   height: '150px',
    width: '150px',
    lineWidth: 2,
    fill: '#0d3c9b',
    dataSource:   [0, 6, 4, 1, 3, 2, 5],
    rangeBandSettings: [
            {
                startRange: 1,
                endRange: 2,
                color: '#bfd4fc',
                opacity:0.4
            },
            {
                startRange: 4,
                endRange: 5,
                color: 'red',
                opacity:0.4
            }
        ]
}, '#element');
```

{% endtab %}
