# Localization

The sparkline control supports localization. The default culture for localization is `en-US`. You can change the culture using the `setCulture` method.

## Tooltip format

Sparkline tooltip supports localization. The following code sample shows tooltip text with currency format based on culture.

{% tab template="sparkline/localization", sourceFiles="index.ts,index.html" , es5Template="es5Localization" %}

```typescript
import { Sparkline, SparklineTooltip } from '@syncfusion/ej2-charts';
Sparkline.Inject(SparklineTooltip);
let sparkline: Sparkline = new Sparkline({
    containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    tooltipSettings: {
        visible: true
    },
    // To specify currency format
    format: 'c0',
    useGroupingSeparator: true,
    lineWidth: 3,
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Area',
    fill: '#b2cfff',
    dataSource: [30000, 60000, 40000, 10000, 30000, 20000, 50000]
}, '#element');
```

{% endtab %}

## RTL

If you set the `enableRtl` property to true, then the sparkline will be rendered from right-to-left direction.

The following example shows the sparkline is render from "Right-to-left".

{% tab template="sparkline/localization", sourceFiles="index.ts,index.html" , es5Template="es5Rtl" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    height: '150px',
    width: '150px',
    enableRtl: true,
    dataSource:   [0, 6, 4, 1, 3, 2, 5]
}, '#element');
```

{% endtab %}