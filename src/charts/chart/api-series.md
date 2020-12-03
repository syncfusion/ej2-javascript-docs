# Series

 Configures the series in charts.

## Properties

### animation [`AnimationModel`](./api-animationModel.html)

Options to customizing animation for the series.

### bearFillColor `string`

This property is used in financial charts to visualize the price movements in stock.
It defines the color of the candle/point, when the opening price is less than the closing price.

Defaults to *'#2ecd71'*

### binInterval `number`

The bin interval of each histogram points.

Defaults to *null*

### border [`BorderModel`](./api-borderModel.html)

Options to customizing the border of the series. This is applicable only for `Column` and `Bar` type series.

### boxPlotMode `string`

The mode of the box and whisker char series. They are,
Exclusive
Inclusive
Normal

Defaults to *'Normal'*

### bullFillColor `string`

This property is used in financial charts to visualize the price movements in stock.
It defines the color of the candle/point, when the opening price is higher than the closing price.

Defaults to *'#e74c3d'*

### cardinalSplineTension `number`

It defines tension of cardinal spline types

Defaults to *0.5*

### close `string`

The DataSource field that contains the close value of y
It is applicable for series and technical indicators

Defaults to *''*

### columnSpacing `number`

To render the column series points with particular column spacing. It takes value from 0 - 1.

Defaults to *0*

### columnWidth `number`

To render the column series points with particular column width. If the series type is histogram the
default value is 1 otherwise 0.7.

Defaults to *null*

### connector [`ConnectorModel`](./api-connectorModel.html)

Defines the appearance of line connecting adjacent points in waterfall charts.

### cornerRadius [`CornerRadiusModel`](./api-cornerRadiusModel.html)

To render the column series points with particular rounded corner.

### dashArray `string`

Defines the pattern of dashes and gaps to stroke the lines in `Line` type series.

Defaults to *'0'*

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

Defaults to *''*

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

Defaults to *'Line'*

### emptyPointSettings [`EmptyPointSettingsModel`](./api-emptyPointSettingsModel.html)

options to customize the empty points in series

### enableSolidCandles `boolean`

This property is applicable for candle series.
It enables/disables to visually compare the current values with the previous values in stock.

Defaults to *false*

### enableTooltip `boolean`

If set true, the Tooltip for series will be visible.

Defaults to *true*

### errorBar [`ErrorBarSettingsModel`](./api-errorBarSettingsModel.html)

Options for displaying and customizing error bar for individual point in a series.

### fill `string`

The fill color for the series that accepts value in hex and rgba as a valid CSS color string.
It also represents the color of the signal lines in technical indicators.
For technical indicators, the default value is 'blue' and for series, it has null.

Defaults to *null*

### high `string`

The DataSource field that contains the high value of y
It is applicable for series and technical indicators

Defaults to *''*

### intermediateSumIndexes `number[]`

Defines the collection of indexes of the intermediate summary columns in waterfall charts.

Defaults to *[]*

### isClosed `boolean`

Specifies whether to join start and end point of a line/area series used in polar/radar chart to form a closed path.

Defaults to *true*

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

Defaults to *'SeriesType'*

### low `string`

The DataSource field that contains the low value of y
It is applicable for series and technical indicators

Defaults to *''*

### marker [`MarkerSettingsModel`](./api-markerSettingsModel.html)

Options for displaying and customizing markers for individual points in a series.

### maxRadius `number`

Maximum radius

Defaults to *3*

### minRadius `number`

Minimum radius

Defaults to *1*

### name `string`

The name of the series visible in legend.

Defaults to *''*

### negativeFillColor `string`

Defines the visual representation of the negative changes in waterfall charts.

Defaults to *'#C64E4A'*

### opacity `number`

The opacity of the series.

Defaults to *1*

### open `string`

The DataSource field that contains the open value of y
It is applicable for series and technical indicators

Defaults to *''*

### pointColorMapping `string`

The DataSource field that contains the color value of point
It is applicable for series

Defaults to *''*

### query `Query`

Specifies query to select data from DataSource. This property is applicable only when the DataSource is `ej.DataManager`.

Defaults to *null*

### segmentAxis `string`

Defines the axis, based on which the line series will be split.

### segments `ChartSegmentModel[]`

Defines the collection of regions that helps to differentiate a line series.

### selectionStyle `string`

Custom style for the selected series or points.

Defaults to *null*

### showMean `boolean`

If set true, the mean value for box and whisker will be visible.

Defaults to *true*

### showNormalDistribution `boolean`

The normal distribution of histogram series.

Defaults to *false*

### size `string`

The DataSource field that contains the size value of y

Defaults to *''*

### splineType `string`

Defines type of spline to be rendered.

Defaults to *'Natural'*

### stackingGroup `string`

This property allows grouping series in `stacked column / bar` charts.
Any string value can be provided to the stackingGroup property.
If any two or above series have the same value, those series will be grouped together.

Defaults to *''*

### sumIndexes `number[]`

Defines the collection of indexes of the overall summary columns in waterfall charts.

Defaults to *[]*

### summaryFillColor `string`

Defines the visual representation of the summaries in waterfall charts.

Defaults to *'#4E81BC'*

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

Defaults to *'Line'*

### visible `boolean`

Specifies the visibility of series.

Defaults to *true*

### volume `string`

Defines the data source field that contains the volume value in candle charts
It is applicable for financial series and technical indicators

Defaults to *''*

### width `number`

The stroke width for the series that is applicable only for `Line` type series.
It also represents the stroke width of the signal lines in technical indicators.

Defaults to *1*

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

Defaults to *null*

### xName `string`

The DataSource field that contains the x value.
It is applicable for series and technical indicators

Defaults to *''*

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

Defaults to *null*

### yName `string`

The DataSource field that contains the y value.

Defaults to *''*
