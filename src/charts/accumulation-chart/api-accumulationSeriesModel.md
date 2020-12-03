# AccumulationSeriesModel

Interface for a class AccumulationSeries

## Properties

### animation `AnimationModel`

Options for customizing the animation for series.

### border `BorderModel`

Options for customizing the border of the series.

### dataLabel [`AccumulationDataLabelSettingsModel`](./api-accumulationDataLabelSettingsModel.html)

The data label for the series.

### dataSource `Object` &#124;  `DataManager`

Specifies the dataSource for the series. It can be an array of JSON objects or an instance of DataManager.
```html
<div id='Pie'></div>
```
```typescript
let dataManager: DataManager = new DataManager({
        url: 'http://mvc.syncfusion.com/Services/Northwnd.svc/Tasks/'
});
let query: Query = new Query().take(50).where('Estimate', 'greaterThan', 0, false);
let pie: AccumulationChart = new AccumulationChart({
...
    series: [{
       dataSource: dataManager,
       xName: 'Id',
       yName: 'Estimate',
       query: query
   }],
...
});
pie.appendTo('#Pie');
```

### emptyPointSettings `EmptyPointSettingsModel`

options to customize the empty points in series

### enableTooltip `boolean`

To enable or disable tooltip for a series.

### endAngle `number`

End angle for a series.

### explode `boolean`

If set true, series points will be exploded on mouse click or touch.

### explodeAll `boolean`

If set true, all the points in the series will get exploded on load.

### explodeIndex `number`

Index of the point, to be exploded on load.

### explodeOffset `string`

Distance of the point from the center, which takes values in both pixels and percentage.

### gapRatio `number`

Defines the distance between the segments of a funnel/pyramid series. The range will be from 0 to 1

### groupMode `string`

AccumulationSeries y values less than groupMode are combined into single slice named others

### groupTo `string`

AccumulationSeries y values less than groupTo are combined into single slice named others

### height `string`

Defines the height of the funnel/pyramid with respect to the chart area

### innerRadius `string`

When the innerRadius value is greater than 0 percentage, a donut will appear in pie series. It takes values only in percentage.

### legendShape `string`

The shape of the legend. Each series has its own legend shape. They are
* Circle - Renders a circle.
* Rectangle - Renders a rectangle.
* Triangle - Renders a triangle.
* Diamond - Renders a diamond.
* Cross - Renders a cross.
* HorizontalLine - Renders a horizontalLine.
* VerticalLine - Renders a verticalLine.
* Pentagon - Renders a pentagon.
* InvertedTriangle - Renders a invertedTriangle.
* SeriesType -Render a legend shape based on series type.

### name `string`

Specifies the series name

### neckHeight `string`

Defines the height of the funnel neck with respect to the chart area

### neckWidth `string`

Defines the width of the funnel neck with respect to the chart area

### opacity `number`

The opacity of the series.

### palettes `string[]`

Palette for series points.

### pointColorMapping `string`

The DataSource field that contains the color value of point
It is applicable for series

### pyramidMode `string`

Defines how the values have to be reflected, whether through height/surface of the segments

### query `Query`

Specifies Query to select data from dataSource. This property is applicable only when the dataSource is `ej.DataManager`.

### radius `string`

Radius of the pie series and its values in percentage.

### selectionStyle `string`

Custom style for the selected series or points.

### startAngle `number`

Start angle for a series.

### type `string`

Specify the type of the series in accumulation chart.

### visible `boolean`

Specifies the series visibility.

### width `string`

Defines the width of the funnel/pyramid with respect to the chart area

### xName `string`

The DataSource field which contains the x value.

### yName `string`

The DataSource field which contains the y value.
