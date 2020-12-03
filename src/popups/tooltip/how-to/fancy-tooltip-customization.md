# Fancy Tooltip Customization

The arrow of the tooltip can be customized as needed by customizing CSS in the sample-side.
The EJ2 tooltip component is achieved through CSS3 format and positioned the tip arrow according to the tooltip positions like `TopCenter`, `BottomLeft`, `RightTop`, and more.

Here, the tip arrow is customized as Curved tooltip and Bubble tooltip.

## Curved tip

The content for the tip pointer arrow has been added. To customize the curved tip arrow, override the following CSS class of tip arrow.

```typescript
    let tooltip: Tooltip = new Tooltip({
    cssClass: 'curvetips e-tooltip-css',
    content: 'Tooltip arrow customized',
});
tooltip.appendTo('#target');
```

```typescript

      .e-arrow-tip-outer.e-tip-bottom,
      .e-arrow-tip-outer.e-tip-top {
           border-left: none !important;
           border-right: none !important;
           border-top: none !important;
      }
      .e-arrow-tip.e-tip-top {
           transform: rotate(170deg);
      }

```

## Bubble tip

The two `divs`(inner div and outer div) have been added to achieve the bubble tip arrow. To customize the bubble tip arrow, override the following CSS class of tip arrow.

```typescript
    let bubble: Tooltip = new Tooltip({
    cssClass: 'bubbletip e-tooltip-css',
    position: 'TopRight',
    content: 'Tooltip arrow customized as balloon tip'
});
bubble.appendTo('#bubbletip');
```

```typescript

    .e-arrow-tip-outer.e-tip-bottom, .e-arrow-tip-outer.e-tip-top
      {
         border-radius: 50px;
         height: 10px;
         width: 10px;
      }

      .e-arrow-tip-inner.e-tip-bottom, .e-arrow-tip-inner.e-tip-top
        {
         border-radius: 50px;
         height: 10px;
         width: 10px;
        }
```

These tip arrow customizations have been achieved through CSS changes in the sample level. The tooltip position can be changed by using the radio button click event.

The arrow tip pointer can also be disabled by using the [`showTipPointer`](../../api/tooltip#showtippointer) property in a tooltip.

{% tab template="tooltip/tip-customization", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="customization-template" %}

```typescript
import { Tooltip } from '@syncfusion/ej2-popups';
import { RadioButton, ChangeArgs, Button } from '@syncfusion/ej2-buttons';

let tooltip: Tooltip = new Tooltip({
   cssClass: 'curvetips e-tooltip-css',
    content: 'Tooltip arrow customized',
});
tooltip.appendTo('#target');

let curvebutton: Button = new Button();
curvebutton.appendTo('#target');

let tipbutton: Button = new Button();
tipbutton.appendTo('#tooltip');

let bubblebutton: Button = new Button();
bubblebutton.appendTo('#bubbletip');

let radiobutton: RadioButton = new RadioButton({ label: 'TopCenter', name: 'default', value: 'TopCenter', checked: true, change: onChange});

// Render initialized radio button
radiobutton.appendTo('#element1');

let radiobutton = new RadioButton({ label: 'BottomLeft', name: 'default', value: 'BottomLeft',  change: onChange});
radiobutton.appendTo('#element2');

let tippointer: Tooltip = new Tooltip({
    cssClass: 'pointertip e-tooltip-css',
    mouseTrail: true,
    content: 'Disabled tooltip pointer',
    showTipPointer: false
});
tippointer.appendTo('#tooltip');

let bubble: Tooltip = new Tooltip({
    cssClass: 'bubbletip e-tooltip-css',
    position: 'TopRight',
    content: 'Tooltip arrow customized as balloon tip'
});
bubble.appendTo('#bubbletip');

let radiobutton: RadioButton = new RadioButton({ label: 'BottomLeft', name: 'position', value: 'BottomLeft', change: onChanged});

// Render initialized radio button
radiobutton.appendTo('#radio1');

let radiobutton = new RadioButton({ label: 'TopRight', name: 'position', value: 'TopRight',  checked: true, change: onChanged});
radiobutton.appendTo('#radio2');

function onChange(args: ChangeArgs): void {
    tooltip.position = args.value as any;
    tooltip.dataBind();
}
function onChanged(args: ChangeArgs): void {
    bubble.position = args.value as any;
    if(bubble.position == 'BottomLeft'){
      bubble.offsetY = -30;
    } else {
      bubble.offsetY = 0;
    }
    bubble.dataBind();
}

```

{% endtab %}