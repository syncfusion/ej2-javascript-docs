# TooltipSettingsModel

Interface for a class TooltipSettings

## Properties

### border [`BorderModel`](./api-borderModel.html)

Options to customize tooltip borders.

### enable `boolean`

Enables / Disables the visibility of the tooltip.

### enableAnimation `boolean`

If set to true, ToolTip will animate while moving from one point to another.

### fill `string`

The fill color of the tooltip that accepts value in hex and rgba as a valid CSS color string.

### format `string`

Format the ToolTip content.

### header `string`

Header for tooltip.

### opacity `number`

The fill color of the tooltip that accepts value in hex and rgba as a valid CSS color string.

### shared `boolean`

If set to true, a single ToolTip will be displayed for every index.

### template `string`

Custom template to format the ToolTip content. Use ${x} and ${y} as the placeholder text to display the corresponding data point.

### textStyle [`FontModel`](./api-fontModel.html)

Options to customize the ToolTip text.
