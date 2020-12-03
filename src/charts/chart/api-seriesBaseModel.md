# SeriesBaseModel

Interface for a class SeriesBase

## Properties

### animation [`AnimationModel`](./api-animationModel.html)

Options to customizing animation for the series.

### close `string`

The DataSource field that contains the close value of y
It is applicable for series and technical indicators

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

### fill `string`

The fill color for the series that accepts value in hex and rgba as a valid CSS color string.
It also represents the color of the signal lines in technical indicators.
For technical indicators, the default value is 'blue' and for series, it has null.

### high `string`

The DataSource field that contains the high value of y
It is applicable for series and technical indicators

### low `string`

The DataSource field that contains the low value of y
It is applicable for series and technical indicators

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
