---
title: " User Interactions in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the User Interaction feature of Syncfusion EJ2 Linear Gauge component and more."
---

# User Interaction in EJ2 Linear Gauge

## Tooltip

<!-- markdownlint-disable MD036 -->

Linear gauge displays the details about a pointer value through [`tooltip`](../api/linear-gauge/tooltipSettings) object, when the mouse hovers over the pointer. To enable the tooltip, set the [`enable`](../api/linear-gauge/tooltipSettings/#enable-boolean) property to "**true**" and inject the **GaugeTooltip** module in Linear Gauge.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5Tooltip" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
   tooltip: {
       enable: true
   },
   axes: [{
        pointers: [{
            value: 80
        }]
    }]
}, '#element');

```

{% endtab %}

<!-- markdownlint-disable MD013 -->

### Tooltip Format

<!-- markdownlint-disable MD013 -->

Tooltip in the Linear Gauge control can be formatted using the [`format`](../api/linear-gauge/tooltipSettings/#format) property in [`tooltip`](../api/linear-gauge/tooltipSettings/) object. It is used to render the tooltip in certain format or to add a user-defined unit in the tooltip. By default, the tooltip shows the pointer value only. In addition to that, more information can be added in the tooltip. For example, the format "**{value}km**" shows pointer value with kilometer unit in the tooltip.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipFormat" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
       enable: true,
       format: '{value}km'
   },
   axes: [{
        pointers: [{
            value: 80
        }]
    }]
}, '#element');

```

{% endtab %}

### Tooltip Template

The HTML element can be rendered in the tooltip of the Linear Gauge using the [`template`](../api/linear-gauge/tooltipSettings/#template) property in the [`tooltip`](../api/linear-gauge/tooltipSettings) . The "**${value}**" can be used as placeholders in the HTML element to display the pointer values of the corresponding axis.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipTemplate" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
            enable: true,
            //tooltip template for Linear gauge
            template: '<div>Pointer: 80 </div>'
        },
        axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

### Customize the appearance of the tooltip

The tooltip can be customized using the following properties in [`tooltip`](../api/linear-gauge/tooltipSettings) object.

* [`fill`](../api/linear-gauge/tooltipSettings/#fill) - To fill the color for tooltip.
* [`enableAnimation`](../api/linear-gauge/tooltipSettings/#enableanimation) - To enable or disable the tooltip animation.
* [`border`](../api/linear-gauge/tooltipSettings/#border) - To set the color and width for the border of the tooltip.
* [`textStyle`](../api/linear-gauge/tooltipSettings/#textstyle) - To customize the style of the text in tooltip.
* [`showAtMousePosition`](../api/linear-gauge/tooltipSettings/#showatmouseposition) - To show the tooltip at the mouse position.

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipCustomize" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
            enable: true,
            fill: '#e5bcbc',
            border: {
                color: '#d80000',
                width: 2
            }
        },
        axes: [{
            pointers: [{
                value: 80
            }]
        }]
}, '#element');

```

{% endtab %}

### Positioning the tooltip

The tooltip is positioned at the "**End**" of the pointer. To change the position of the tooltip at the start, or center of the pointer, set the [`position`](../api/linear-gauge/tooltipSettings/#position) property to "**Start**" or "**Center**".

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5TooltipPosition" %}

```typescript
import { LinearGauge, GaugeTooltip } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(GaugeTooltip);
let gauge: LinearGauge = new LinearGauge({
    tooltip: {
        enable: true,
        position: "Center"
    },
    axes: [{
        pointers: [{
            type: 'Bar',
            value: 50,
            offset: -50,
            color: "red"
        }],
        majorTicks: {
            interval: 10
        },
        minorTicks: {
            interval: 2
        },
        labelStyle: {
            offset: 48
        }
    }],
}, '#element');

```

{% endtab %}

## Pointer Drag

To drag either the marker or bar pointer to the desired axis value, set the [`enableDrag`](../api/linear-gauge/pointer/#enabledrag) property as "**true**" in the [`pointer`](../api/linear-gauge/pointerModel/).

{% tab template= "linear-gauge/user-interaction", sourceFiles="index.ts,index.html", es5Template="es5PointerDrag" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes: [{
        pointers: [{
            value: 80,
            enableDrag: true
        }]
    }]
}, '#element');

```

{% endtab %}