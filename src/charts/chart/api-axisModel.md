# AxisModel

Interface for a class Axis

## Properties

### border [`LabelBorderModel`](./api-labelBorderModel.html)

Border of the multi level labels.

### coefficient `number`

The polar radar radius position.

### columnIndex `number`

Specifies the index of the column where the axis is associated,
when the chart area is divided into multiple plot areas by using `columns`.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
    columns: [{ width: '50%' },
              { width: '50%' }],
    axes: [{
               name: 'xAxis 1',
               columnIndex: 1,
    }],
...
});
chart.appendTo('#Chart');
```

### crossesAt `Object`

Specifies the value at which the axis line has to be intersect with the vertical axis or vice versa.

### crossesInAxis `string`

Specifies axis name with which the axis line has to be crossed

### crosshairTooltip [`CrosshairTooltipModel`](./api-crosshairTooltipModel.html)

Options to customize the crosshair ToolTip.

### description `string`

Description for axis and its element.

### desiredIntervals `number`

With this property, you can request axis to calculate intervals approximately equal to your specified interval.

### edgeLabelPlacement `string`

Specifies the position of labels at the edge of the axis.They are,
* None: No action will be performed.
* Hide: Edge label will be hidden.
* Shift: Shifts the edge labels.

### enableAutoIntervalOnZooming `boolean`

If set to true, axis interval will be calculated automatically with respect to the zoomed range.

### interval `number`

Specifies the interval for an axis.

### intervalType `string`

Specifies the types like `Years`, `Months`, `Days`, `Hours`, `Minutes`, `Seconds` in date time axis.They are,
* Auto: Defines the interval of the axis based on data.
* Years: Defines the interval of the axis in years.
* Months: Defines the interval of the axis in months.
* Days: Defines the interval of the axis in days.
* Hours: Defines the interval of the axis in hours.
* Minutes: Defines the interval of the axis in minutes.

### isIndexed `boolean`

Specifies indexed category  axis.

### isInversed `boolean`

It specifies whether the axis to be rendered in inversed manner or not.

### labelFormat `string`

Used to format the axis label that accepts any global string format like 'C', 'n1', 'P' etc.
It also accepts placeholder like '{value}°C' in which value represent the axis label, e.g, 20°C.

### labelIntersectAction `string`

Specifies the actions like `Hide`, `Rotate45`, and `Rotate90` when the axis labels intersect with each other.They are,
* None: Shows all the labels.
* Hide: Hides the label when it intersects.
* Rotate45: Rotates the label to 45 degree when it intersects.
* Rotate90: Rotates the label to 90 degree when it intersects.

### labelPlacement `string`

Specifies the placement of a label for category axis. They are,
* betweenTicks: Renders the label between the ticks.
* onTicks: Renders the label on the ticks.

### labelPosition `string`

Specifies the placement of a labels to the axis line. They are,
* inside: Renders the labels inside to the axis line.
* outside: Renders the labels outside to the axis line.

### labelRotation `number`

The angle to which the axis label gets rotated.

### labelStyle [`FontModel`](./api-fontModel.html)

Options to customize the axis label.

### lineStyle [`AxisLineModel`](./api-axisLineModel.html)

Options for customizing axis lines.

### logBase `number`

The base value for logarithmic axis. It requires `valueType` to be `Logarithmic`.

### majorGridLines [`MajorGridLinesModel`](./api-majorGridLinesModel.html)

Options for customizing major grid lines.

### majorTickLines [`MajorTickLinesModel`](./api-majorTickLinesModel.html)

Options for customizing major tick lines.

### maximum `Object`

Specifies the maximum range of an axis.

### maximumLabels `number`

The maximum number of label count per 100 pixels with respect to the axis length.

### minimum `Object`

Specifies the minimum range of an axis.

### minorGridLines [`MinorGridLinesModel`](./api-minorGridLinesModel.html)

Options for customizing minor grid lines.

### minorTickLines [`MinorTickLinesModel`](./api-minorTickLinesModel.html)

Options for customizing minor tick lines.

### minorTicksPerInterval `number`

Specifies the number of minor ticks per interval.

### multiLevelLabels `MultiLevelLabelsModel[]`

Specifies the multi level labels collection for the axis

### name `string`

Unique identifier of an axis.
To associate an axis with the series, set this name to the xAxisName/yAxisName properties of the series.

### opposedPosition `boolean`

If set to true, the axis will render at the opposite side of its default position.

### placeNextToAxisLine `boolean`

Specifies whether axis elements like axis labels, axis title, etc has to be crossed with axis line

### plotOffset `number`

Left and right padding for the plot area in pixels.

### rangePadding `string`

Specifies the padding for the axis range in terms of interval.They are,
* none: Padding cannot be applied to the axis.
* normal: Padding is applied to the axis based on the range calculation.
* additional: Interval of the axis is added as padding to the minimum and maximum values of the range.
* round: Axis range is rounded to the nearest possible value divided by the interval.

### rowIndex `number`

Specifies the index of the row where the axis is associated, when the chart area is divided into multiple plot areas by using `rows`.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
    rows: [{ height: '50%' },
           { height: '50%' }],
    axes: [{
               name: 'yAxis 1',
               rowIndex: 1,
     }],
...
});
chart.appendTo('#Chart');
```

### skeleton `string`

Specifies the skeleton format in which the dateTime format will process.

### skeletonType `string`

It specifies the type of format to be used in dateTime format process.

### span `number`

Specifies the number of `columns` or `rows` an axis has to span horizontally or vertically.

### startAngle `number`

The start angle for the series.

### stripLines `StripLineSettingsModel[]`

Specifies the stripLine collection for the axis

### tabIndex `number`

TabIndex value for the axis.

### tickPosition `string`

Specifies the placement of a ticks to the axis line. They are,
* inside: Renders the ticks inside to the axis line.
* outside: Renders the ticks outside to the axis line.

### title `string`

Specifies the title of an axis.

### titleStyle [`FontModel`](./api-fontModel.html)

Options for customizing the axis title.

### valueType `string`

Specifies the type of data the axis is handling.
* Double:  Renders a numeric axis.
* DateTime: Renders a dateTime axis.
* Category: Renders a category axis.
* Logarithmic: Renders a log axis.

### visible `boolean`

If set to true, axis label will be visible.

### zoomFactor `number`

The axis is scaled by this factor. When zoomFactor is 0.5, the chart is scaled by 200% along this axis. Value ranges from 0 to 1.

### zoomPosition `number`

Position of the zoomed axis. Value ranges from 0 to 1.
