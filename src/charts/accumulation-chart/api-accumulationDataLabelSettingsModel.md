# AccumulationDataLabelSettingsModel

Interface for a class AccumulationDataLabelSettings

## Properties

### border `BorderModel`

Option for customizing the border lines.

### connectorStyle `ConnectorModel`

Options for customize the connector line in series.
This property is applicable for Pie, Funnel and Pyramid series.
The default connector length for Pie series is '4%'. For other series, it is null.

### fill `string`

The background color of the data label, which accepts value in hex, rgba as a valid CSS color string.

### font `FontModel`

Option for customizing the data label text.

### name `string`

The DataSource field which contains the data label value.

### position `string`

Specifies the position of data label. They are.
* Outside - Places label outside the point.
* Inside - Places label inside the point.

### rx `number`

The roundedCornerX for the data label. It requires `border` values not to be null.

### ry `number`

The roundedCornerY for the data label. It requires `border` values not to be null.

### template `string`

Custom template to format the data label content. Use ${point.x} and ${point.y} as a placeholder
text to display the corresponding data point.

### visible `boolean`

If set true, data label for series gets render.
