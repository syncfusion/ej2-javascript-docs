# TooltipSettings

Configures the ToolTips in the chart.

## Properties

### border [`BorderModel`](./api-borderModel.html)

Options to customize tooltip borders.

### enable `boolean`

Enables / Disables the visibility of the tooltip.

Defaults to *false.*

### enableAnimation `boolean`

If set to true, ToolTip will animate while moving from one point to another.

Defaults to *true.*

### fill `string`

The fill color of the tooltip that accepts value in hex and rgba as a valid CSS color string.

Defaults to *null*

### format `string`

Format the ToolTip content.

Defaults to *null.*

### header `string`

Header for tooltip.

Defaults to *null*

### opacity `number`

The fill color of the tooltip that accepts value in hex and rgba as a valid CSS color string.

Defaults to *0.75*

### shared `boolean`

If set to true, a single ToolTip will be displayed for every index.

Defaults to *false.*

### template `string`

Custom template to format the ToolTip content. Use ${x} and ${y} as the placeholder text to display the corresponding data point.

Defaults to *null.*

### textStyle [`FontModel`](./api-fontModel.html)

Options to customize the ToolTip text.
