# DataLabelSettingsModel

Interface for a class DataLabelSettings

## Properties

### alignment `string`

Specifies the alignment for data Label. They are,
* Near: Aligns the label to the left of the point.
* Center: Aligns the label to the center of the point.
* Far: Aligns the label to the right of the point.

### border [`BorderModel`](./api-borderModel.html)

Option for customizing the border lines.

### fill `string`

The background color of the data label accepts value in hex and rgba as a valid CSS color string.

### font [`FontModel`](./api-fontModel.html)

Option for customizing the data label text.

### margin [`MarginModel`](./api-marginModel.html)

Margin configuration for the data label.

### name `string`

The DataSource field that contains the data label value.

### opacity `number`

The opacity for the background.

### position `string`

Specifies the position of the data label. They are,
* Outer: Positions the label outside the point.
* top: Positions the label on top of the point.
* Bottom: Positions the label at the bottom of the point.
* Middle: Positions the label to the middle of the point.
* Auto: Positions the label based on series.

### rx `number`

The roundedCornerX for the data label. It requires `border` values not to be null.

### ry `number`

The roundedCornerY for the data label. It requires `border` values not to be null.

### template `string`

Custom template to show the data label. Use ${point.x} and ${point.y} as a placeholder
text to display the corresponding data point.

### visible `boolean`

If set true, data label for series renders.
