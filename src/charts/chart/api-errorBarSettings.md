# ErrorBarSettings

## Properties

### color `string`

 The color for stroke of the error bar, which accepts value in hex, rgba as a valid CSS color string.

Defaults to *null*

### direction `string`

The direction of the error bar . They are
* both -  Renders both direction of error bar.
* minus - Renders minus direction of error bar.
* plus - Renders plus direction error bar.

Defaults to *'Both'*

### errorBarCap [`ErrorBarCapSettingsModel`](./api-errorBarCapSettingsModel.html)

Options for customizing the cap of the error bar.

### horizontalError `number`

The horizontal error of the error bar.

Defaults to *1*

### horizontalNegativeError `number`

The horizontal negative error of the error bar.

Defaults to *1*

### horizontalPositiveError `number`

The horizontal positive error of the error bar.

Defaults to *1*

### mode `string`

The mode of the error bar . They are
* Vertical -  Renders a vertical error bar.
* Horizontal - Renders a horizontal error bar.
* Both - Renders both side error bar.

Defaults to *'Vertical'*

### type `string`

The type of the error bar . They are
* Fixed -  Renders a fixed type error bar.
* Percentage - Renders a percentage type error bar.
* StandardDeviation - Renders a standard deviation type error bar.
* StandardError -Renders a standard error type error bar.
* Custom -Renders a custom type error bar.

Defaults to *'Fixed'*

### verticalError `number`

The vertical error of the error bar.

Defaults to *1*

### verticalNegativeError `number`

The vertical negative error of the error bar.

Defaults to *3*

### verticalPositiveError `number`

The vertical positive error of the error bar.

Defaults to *3*

### visible `boolean`

If set true, error bar for data gets rendered.

Defaults to *false*

### width `number`

The stroke width of the error bar..

Defaults to *1*
