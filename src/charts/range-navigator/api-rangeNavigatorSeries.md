# RangeNavigatorSeries

Series class for the range navigator

## Properties

### animation `AnimationModel`

Options to customizing animation for the series.

### border `BorderModel`

Options for customizing the color and width of the series border.

### dashArray `string`

Defines the pattern of dashes and gaps to stroke the lines in `Line` type series.

Defaults to *'0'*

### dataSource `Object` &#124;  `DataManager`

It defines the data source for a series.

Defaults to *null*

### fill `string`

The fill color for the series that accepts value in hex and rgba as a valid CSS color string.
It also represents the color of the signal lines in technical indicators.
For technical indicators, the default value is 'blue' and for series, it has null.

Defaults to *null*

### query `Query`

It defines the query for the data source

Defaults to *null*

### type `string`

It defines the series type of the range navigator

Defaults to *'Line'*

### width `number`

The stroke width for the series that is applicable only for `Line` type series.
It also represents the stroke width of the signal lines in technical indicators.

Defaults to *1*

### xName `string`

It defines the xName for the series

Defaults to *null*

### yName `string`

It defines the yName for the series

Defaults to *null*
