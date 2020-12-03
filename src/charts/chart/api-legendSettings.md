# LegendSettings

Configures the legends in charts.

## Properties

### alignment `string`

Legend in chart can be aligned as follows:
* Near: Aligns the legend to the left of the chart.
* Center: Aligns the legend to the center of the chart.
* Far: Aligns the legend to the right of the chart.

Defaults to *'Center'*

### background `string`

The background color of the legend that accepts value in hex and rgba as a valid CSS color string.

Defaults to *'transparent'*

### border [`BorderModel`](./api-borderModel.html)

Options to customize the border of the legend.

### description `string`

Description for legends.

Defaults to *null*

### height `string`

The height of the legend in pixels.

Defaults to *null*

### location [`LocationModel`](./api-locationModel.html)

Specifies the location of the legend, relative to the chart.
If x is 20, legend moves by 20 pixels to the right of the chart. It requires the `position` to be `Custom`.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
  legendSettings: {
    visible: true,
    position: 'Custom',
    location: { x: 100, y: 150 },
  },
...
});
chart.appendTo('#Chart');
```

### opacity `number`

Opacity of the legend.

Defaults to *1*

### padding `number`

Option to customize the padding between legend items.

Defaults to *8*

### position `string`

Position of the legend in the chart are,
* Auto: Places the legend based on area type.
* Top: Displays the legend at the top of the chart.
* Left: Displays the legend at the left of the chart.
* Bottom: Displays the legend at the bottom of the chart.
* Right: Displays the legend at the right of the chart.
* Custom: Displays the legend  based on the given x and y values.

Defaults to *'Auto'*

### shapeHeight `number`

Shape height of the legend in pixels.

Defaults to *10*

### shapePadding `number`

Padding between the legend shape and text.

Defaults to *5*

### shapeWidth `number`

Shape width of the legend in pixels.

Defaults to *10*

### tabIndex `number`

TabIndex value for the legend.

Defaults to *3*

### textStyle [`FontModel`](./api-fontModel.html)

Options to customize the legend text.

### toggleVisibility `boolean`

If set to true, series' visibility collapses based on the legend visibility.

Defaults to *true*

### visible `boolean`

If set to true, legend will be visible.

Defaults to *true*

### width `string`

The width of the legend in pixels.

Defaults to *null*
