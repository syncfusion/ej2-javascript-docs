# SeriesModel

Interface for a class Series

## Properties

### animation [`AnimationModel`](./api-animationModel.html)

Options to customizing animation for the series.

### bearFillColor `string`

This property is used in financial charts to visualize the price movements in stock.
It defines the color of the candle/point, when the opening price is less than the closing price.

### binInterval `number`

The bin interval of each histogram points.

### border [`BorderModel`](./api-borderModel.html)

Options to customizing the border of the series. This is applicable only for `Column` and `Bar` type series.

### boxPlotMode `string`

The mode of the box and whisker char series. They are,
Exclusive
Inclusive
Normal

### bullFillColor `string`

This property is used in financial charts to visualize the price movements in stock.
It defines the color of the candle/point, when the opening price is higher than the closing price.

### cardinalSplineTension `number`

It defines tension of cardinal spline types

### close `string`

The DataSource field that contains the close value of y
It is applicable for series and technical indicators

### columnSpacing `number`

To render the column series points with particular column spacing. It takes value from 0 - 1.

### columnWidth `number`

To render the column series points with particular column width. If the series type is histogram the
default value is 1 otherwise 0.7.

### connector [`ConnectorModel`](./api-connectorModel.html)

Defines the appearance of line connecting adjacent points in waterfall charts.

### cornerRadius [`CornerRadiusModel`](./api-cornerRadiusModel.html)

To render the column series points with particular rounded corner.

### dashArray `string`

Defines the pattern of dashes and gaps to stroke the lines in `Line` type series.

### dataSource `Object` &#124;  `DataManager`

Specifies the DataSource for the series. It can be an array of JSON objects or an instance of DataManager.
```html
<div id='Chart'></div>
```
```typescript
let dataManager: DataManager = new DataManager({
        url: 'http://mvc.syncfusion.com/Services/Northwnd.svc/Tasks/'
});
let query: Query = new Query().take(50).where('Estimate', 'greaterThan', 0, false);
let chart: Chart = new Chart({
...
    series: [{
       dataSource: dataManager,
       xName: 'Id',
       yName: 'Estimate',
       query: query
   }],
...
});
chart.appendTo('#Chart');
```

### drawType `string`

Type of series to be drawn in radar or polar series. They are
 'Line'
 'Column'
 'Area'
 'Scatter'
 'Spline'
 'StackingColumn'
 'StackingArea'
 'RangeColumn'
 'SplineArea'

### emptyPointSettings [`EmptyPointSettingsModel`](./api-emptyPointSettingsModel.html)

options to customize the empty points in series

### enableSolidCandles `boolean`

This property is applicable for candle series.
It enables/disables to visually compare the current values with the previous values in stock.

### enableTooltip `boolean`

If set true, the Tooltip for series will be visible.

### errorBar [`ErrorBarSettingsModel`](./api-errorBarSettingsModel.html)

Options for displaying and customizing error bar for individual point in a series.

### fill `string`

The fill color for the series that accepts value in hex and rgba as a valid CSS color string.
It also represents the color of the signal lines in technical indicators.
For technical indicators, the default value is 'blue' and for series, it has null.

### high `string`

The DataSource field that contains the high value of y
It is applicable for series and technical indicators

### intermediateSumIndexes `number[]`

Defines the collection of indexes of the intermediate summary columns in waterfall charts.

### isClosed `boolean`

Specifies whether to join start and end point of a line/area series used in polar/radar chart to form a closed path.

### legendShape `string`

The shape of the legend. Each series has its own legend shape. They are,
* Circle
* Rectangle
* Triangle
* Diamond
* Cross
* HorizontalLine
* VerticalLine
* Pentagon
* InvertedTriangle
* SeriesType

### low `string`

The DataSource field that contains the low value of y
It is applicable for series and technical indicators

### marker [`MarkerSettingsModel`](./api-markerSettingsModel.html)

Options for displaying and customizing markers for individual points in a series.

### maxRadius `number`

Maximum radius

### minRadius `number`

Minimum radius

### name `string`

The name of the series visible in legend.

### negativeFillColor `string`

Defines the visual representation of the negative changes in waterfall charts.

### opacity `number`

The opacity of the series.

### open `string`

The DataSource field that contains the open value of y
It is applicable for series and technical indicators

### pointColorMapping `string`

The DataSource field that contains the color value of point
It is applicable for series

### query `Query`

Specifies query to select data from DataSource. This property is applicable only when the DataSource is `ej.DataManager`.

### segmentAxis `string`

Defines the axis, based on which the line series will be split.

### segments `ChartSegmentModel[]`

Defines the collection of regions that helps to differentiate a line series.

### selectionStyle `string`

Custom style for the selected series or points.

### showMean `boolean`

If set true, the mean value for box and whisker will be visible.

### showNormalDistribution `boolean`

The normal distribution of histogram series.

### size `string`

The DataSource field that contains the size value of y

### splineType `string`

Defines type of spline to be rendered.

### stackingGroup `string`

This property allows grouping series in `stacked column / bar` charts.
Any string value can be provided to the stackingGroup property.
If any two or above series have the same value, those series will be grouped together.

### sumIndexes `number[]`

Defines the collection of indexes of the overall summary columns in waterfall charts.

### summaryFillColor `string`

Defines the visual representation of the summaries in waterfall charts.

### trendlines `TrendlineModel[]`

Defines the collection of trendlines that are used to predict the trend

### type `string`

The type of the series are
* Line
* Column
* Area
* Bar
* Histogram
* StackingColumn
* StackingArea
* StackingBar
* StepLine
* StepArea
* Scatter
* Spline
* StackingColumn100
* StackingBar100
* StackingArea100
* RangeColumn
* Hilo
* HiloOpenClose
* Waterfall
* RangeArea
* Bubble
* Candle
* Polar
* Radar
* BoxAndWhisker

### visible `boolean`

Specifies the visibility of series.

### volume `string`

Defines the data source field that contains the volume value in candle charts
It is applicable for financial series and technical indicators

### width `number`

The stroke width for the series that is applicable only for `Line` type series.
It also represents the stroke width of the signal lines in technical indicators.

### xAxisName `string`

The name of the horizontal axis associated with the series. It requires `axes` of the chart.
It is applicable for series and technical indicators
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
    series: [{
               dataSource: data,
               xName: 'x', yName: 'y',
               xAxisName: 'xAxis 1',
    }],
});
chart.appendTo('#Chart');
```

### xName `string`

The DataSource field that contains the x value.
It is applicable for series and technical indicators

### yAxisName `string`

The name of the vertical axis associated with the series. It requires `axes` of the chart.
It is applicable for series and technical indicators
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
    series: [{
               dataSource: data,
               xName: 'x', yName: 'y',
               yAxisName: 'yAxis 1'
    }],
});
chart.appendTo('#Chart');
```

### yName `string`

The DataSource field that contains the y value.
