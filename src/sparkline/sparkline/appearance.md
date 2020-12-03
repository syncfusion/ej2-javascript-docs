# Appearance

The appearance of the sparkline can be customized using margin, containerArea border, and containerArea background.

## Sparkline border

The `containerArea border` of the sparkline is used to render border to cover sparkline area.

The following code example shows the sparkline with overall border.

{% tab template= "sparkline/appearance", sourceFiles="index.ts,index.html" , es5Template="es5Border" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    // To render border around the sparkline
    containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    border: { color: '#033e96', width: 1 },
    height: '200px',
    width: '350px',
    type: 'Area',
    fill: '#b2cfff',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
}, '#element');
```

{% endtab %}

## Sparkline padding

Padding is used to specify padding value between container and sparkline. By default, padding value of the sparkline is 5. Sparkline `padding` values are specified by the left, right, top, and bottom.

The following code example shows the sparkline with overall padding is set to 20.

{% tab template= "sparkline/appearance", sourceFiles="index.ts,index.html", es5Template="es5Padding" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    containerArea: {
        border: { color: '#033e96', width: 2 }
    },
    // To render sparkline with padding
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 1 },
    height: '200px',
    width: '350px',
    type: 'Area',
    fill: '#b2cfff',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
}, '#element');
```

{% endtab %}

## Sparkline area customization

The background color of the sparkline area can be customized using the `containerArea background` color. By default, the sparkline background color is `transparent`.

{% tab template= "sparkline/appearance", sourceFiles="index.ts,index.html" , es5Template="es5Customization" %}

```typescript
import { Sparkline } from '@syncfusion/ej2-charts';
let sparkline: Sparkline = new Sparkline({
    containerArea: {
        border: { color: '#033e96', width: 2 },
        // To render sparkline with background
        background: '#eff1f4',
    },
    padding: { left: 20, right: 20, bottom: 20, top: 20},
    border: { color: '#033e96', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Area',
    fill: '#b2cfff',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
}, '#element');
```

{% endtab %}

## Sparkline theme

Datalabel and trackline colors of the sparkline will be changed based on theme. For example, for dark theme, the color of datalabel and trackline should be white; for light theme, their value should be black. The possible values for sparkline theme are `Material`, `Fabric`, `Bootstrap`, and `Highcontrast`.

The following code example shows the color for datalabel and trackline is set to white for dark theme.

{% tab template= "sparkline/appearance", sourceFiles="index.ts,index.html" , es5Template="es5Theme" %}

```typescript
import { Sparkline, SparklineTooltip } from '@syncfusion/ej2-charts';
Sparkline.Inject(SparklineTooltip);
document.getElementById('container').style = 'background: #000000; margin-top: 15%;';
let sparkline: Sparkline = new Sparkline({
    // To specify theme
    theme: 'Highcontrast',
    dataLabelSettings: { visible: ['All']},
    tooltipSettings: {
        trackLineSettings: { visible: true }
    },
    axisSettings: {
        minX: -1, maxX: 7
    },
    lineWidth: 3,
    border: { color: 'transparent', width: 2 },
    height: '200px',
    width: '350px',
    type: 'Line',
    fill: '#007dd1',
    dataSource: [3, 6, 4, 1, 3, 2, 5]
}, '#element');
```

{% endtab %}