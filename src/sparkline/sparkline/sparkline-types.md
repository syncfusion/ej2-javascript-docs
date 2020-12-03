# Sparkline Types

Different types of shapes can be used to represent the sparkline. You can change the sparkline type by setting the type property. Sparkline supports the following types:

* Line
* Column
* Win-Loss
* Pie
* Area

The following code sample shows different types of sparklines.

<!-- markdownlint-disable MD036 -->

**Line**

The [`Line`] type is used to render the sparkline series as line.

{% tab template= "sparkline/sparkline-types", sourceFiles="index.ts,index.html" , es5Template="es5Line" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'Line' as type of the sparkline
    type:'Line'
}, '#element');
```

{% endtab %}

**Column**

The [`Column`] type is used to render the sparkline series as column.

{% tab template= "sparkline/sparkline-types", sourceFiles="index.ts,index.html" , es5Template="es5Column" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '150px',
    width: '200px',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'Column' as type of the sparkline
    type:'Column'
}, '#element');
```

{% endtab %}

**Pie**

The [`Pie`] type is used to render the sparkline series as pie.

{% tab template= "sparkline/sparkline-types", sourceFiles="index.ts,index.html" , es5Template="es5Pie" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '200px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'Pie' as type of the sparkline
    type:'Pie'
}, '#element');
```

{% endtab %}

**WinLoss**

The [`WinLoss`] type is used to render the sparkline series as WinLoss.

{% tab template= "sparkline/sparkline-types", sourceFiles="index.ts,index.html" , es5Template="es5WinLoss" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: -20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: -21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: -22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'WinLoss' as type of the sparkline
    type:'WinLoss'
}, '#element');
```

{% endtab %}

**Area**

The [`Area`] type is used to render the sparkline series as area.

{% tab template= "sparkline/sparkline-types", sourceFiles="index.ts,index.html" , es5Template="es5Area" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '100px',
    width: '70%',
    dataSource: [
            { x: 0, xval: '2005', yval: 20090440 },
            { x: 1, xval: '2006', yval: 20264080 },
            { x: 2, xval: '2007', yval: 20434180 },
            { x: 3, xval: '2008', yval: 21007310 },
            { x: 4, xval: '2009', yval: 21262640 },
            { x: 5, xval: '2010', yval: 21515750 },
            { x: 6, xval: '2011', yval: 21766710 },
            { x: 7, xval: '2012', yval: 22015580 },
            { x: 8, xval: '2013', yval: 22262500 },
            { x: 9, xval: '2014', yval: 22507620 },
        ],
    // Assign the dataSource values to series of sparkline 'xName and yName'
    xName: 'xval', yName: 'yval',
    // Assign 'Area' as type of the sparkline
    type:'Area'
}, '#element');
```

{% endtab %}