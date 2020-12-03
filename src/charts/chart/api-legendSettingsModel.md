# LegendSettingsModel

Interface for a class LegendSettings

## Properties

### alignment `string`

Legend in chart can be aligned as follows:
* Near: Aligns the legend to the left of the chart.
* Center: Aligns the legend to the center of the chart.
* Far: Aligns the legend to the right of the chart.

### background `string`

The background color of the legend that accepts value in hex and rgba as a valid CSS color string.

### border [`BorderModel`](./api-borderModel.html)

Options to customize the border of the legend.

### description `string`

Description for legends.

### height `string`

The height of the legend in pixels.

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

### padding `number`

Option to customize the padding between legend items.

### position `string`

Position of the legend in the chart are,
* Auto: Places the legend based on area type.
* Top: Displays the legend at the top of the chart.
* Left: Displays the legend at the left of the chart.
* Bottom: Displays the legend at the bottom of the chart.
* Right: Displays the legend at the right of the chart.
* Custom: Displays the legend  based on the given x and y values.

### shapeHeight `number`

Shape height of the legend in pixels.

### shapePadding `number`

Padding between the legend shape and text.

### shapeWidth `number`

Shape width of the legend in pixels.

### tabIndex `number`

TabIndex value for the legend.

### textStyle [`FontModel`](./api-fontModel.html)

Options to customize the legend text.

### toggleVisibility `boolean`

If set to true, series' visibility collapses based on the legend visibility.

### visible `boolean`

If set to true, legend will be visible.

### width `string`

The width of the legend in pixels.
