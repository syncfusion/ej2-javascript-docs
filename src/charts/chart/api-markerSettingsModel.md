# MarkerSettingsModel

Interface for a class MarkerSettings

## Properties

### border [`BorderModel`](./api-borderModel.html)

Options for customizing the border of a marker.

### dataLabel [`DataLabelSettingsModel`](./api-dataLabelSettingsModel.html)

The data label for the series.

### fill `string`

 The fill color of the marker that accepts value in hex and rgba as a valid CSS color string. By default, it will take series' color.

### height `number`

The height of the marker in pixels.

### imageUrl `string`

The URL for the Image that is to be displayed as a marker.  It requires marker `shape` value to be an `Image`.

### opacity `number`

The opacity of the marker.

### shape `string`

The different shape of a marker:
* Circle
* Rectangle
* Triangle
* Diamond
* HorizontalLine
* VerticalLine
* Pentagon
* InvertedTriangle
* Image

### visible `boolean`

If set to true the marker for series is rendered. This is applicable only for line and area type series.

### width `number`

The width of the marker in pixels.
