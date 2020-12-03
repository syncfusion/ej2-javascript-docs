# StripLineSettings

Strip line properties

## Properties

### border [`BorderModel`](./api-borderModel.html)

Border of the strip line.

### color `string`

Color of the strip line.

Defaults to *'#808080'*

### end `number` &#124;  `Date` &#124;  `string`

End value of the strip line.

Defaults to *null*

### horizontalAlignment `string`

Defines the position of the strip line text horizontally. They are,
* Start: Places the strip line text at the start.
* Middle: Places the strip line text in the middle.
* End: Places the strip line text at the end.

Defaults to *'Middle'*

### opacity `number`

Strip line Opacity

Defaults to *1*

### rotation `number`

The angle to which the strip line text gets rotated.

Defaults to *null*

### size `number`

Size of the strip line, when it starts from the origin.

Defaults to *null*

### start `number` &#124;  `Date` &#124;  `string`

Start value of the strip line.

Defaults to *null*

### startFromAxis `boolean`

 If set true, strip line get render from axis origin.
 @default false

### text `string`

Strip line text.

Defaults to *''*

### textStyle [`FontModel`](./api-fontModel.html)

Options to customize the strip line text.

### verticalAlignment `string`

Defines the position of the strip line text vertically. They are,
* Start: Places the strip line text at the start.
* Middle: Places the strip line text in the middle.
* End: Places the strip line text at the end.

Defaults to *'Middle'*

### visible `boolean`

If set true, strip line for axis renders.

Defaults to *true*

### zIndex `string`

Specifies the order of the strip line. They are,
* Behind: Places the strip line behind the series elements.
* Over: Places the strip line over the series elements.

Defaults to *'Behind'*
