# ChartModel

Interface for a class Chart

## Properties

### animationComplete [`EmitType<IAnimationCompleteEventArgs>`](./api-iAnimationCompleteEventArgs.html)

Triggers after animation is completed for the series.

### annotationRender [`EmitType<IAnnotationRenderEventArgs>`](./api-iAnnotationRenderEventArgs.html)

Triggers before the annotation gets rendered.

### axisLabelRender [`EmitType<IAxisLabelRenderEventArgs>`](./api-iAxisLabelRenderEventArgs.html)

Triggers before each axis label is rendered.

### axisMultiLabelRender [`EmitType<IAxisMultiLabelRenderEventArgs>`](./api-iAxisMultiLabelRenderEventArgs.html)

Triggers before each axis multi label is rendered.

### axisRangeCalculated [`EmitType<IAxisRangeCalculatedEventArgs>`](./api-iAxisRangeCalculatedEventArgs.html)

Triggers before each axis range is rendered.

### beforePrint [`EmitType<IPrintEventArgs>`](./api-iPrintEventArgs.html)

Triggers before the prints gets started.

### chartMouseClick [`EmitType<IMouseEventArgs>`](./api-iMouseEventArgs.html)

Triggers on clicking the chart.

### chartMouseDown [`EmitType<IMouseEventArgs>`](./api-iMouseEventArgs.html)

Triggers on mouse down.

### chartMouseLeave [`EmitType<IMouseEventArgs>`](./api-iMouseEventArgs.html)

Triggers when cursor leaves the chart.

### chartMouseMove [`EmitType<IMouseEventArgs>`](./api-iMouseEventArgs.html)

Triggers on hovering the chart.

### chartMouseUp [`EmitType<IMouseEventArgs>`](./api-iMouseEventArgs.html)

Triggers on mouse up.

### dragComplete [`EmitType<IDragCompleteEventArgs>`](./api-iDragCompleteEventArgs.html)

Triggers after the drag selection is completed.

### legendRender [`EmitType<ILegendRenderEventArgs>`](./api-iLegendRenderEventArgs.html)

Triggers before the legend is rendered.

### load [`EmitType<ILoadedEventArgs>`](./api-iLoadedEventArgs.html)

Triggers before chart load.

### loaded [`EmitType<ILoadedEventArgs>`](./api-iLoadedEventArgs.html)

Triggers after chart load.

### pointClick [`EmitType<IPointEventArgs>`](./api-iPointEventArgs.html)

Triggers on point click.

### pointMove [`EmitType<IPointEventArgs>`](./api-iPointEventArgs.html)

Triggers on point move.

### pointRender [`EmitType<IPointRenderEventArgs>`](./api-iPointRenderEventArgs.html)

Triggers before each points for the series is rendered.

### resized [`EmitType<IResizeEventArgs>`](./api-iResizeEventArgs.html)

Triggers after resizing of chart

### seriesRender [`EmitType<ISeriesRenderEventArgs>`](./api-iSeriesRenderEventArgs.html)

Triggers before the series is rendered.

### textRender [`EmitType<ITextRenderEventArgs>`](./api-iTextRenderEventArgs.html)

Triggers before the data label for series is rendered.

### tooltipRender [`EmitType<ITooltipRenderEventArgs>`](./api-iTooltipRenderEventArgs.html)

Triggers before the tooltip for series is rendered.

### zoomComplete [`EmitType<IZoomCompleteEventArgs>`](./api-iZoomCompleteEventArgs.html)

Triggers after the zoom selection is completed.

### annotations `ChartAnnotationSettingsModel[]`

The configuration for annotation in chart.

### axes `AxisModel[]`

Secondary axis collection for the chart.

### background `string`

The background color of the chart that accepts value in hex and rgba as a valid CSS color string.

### border [`BorderModel`](./api-borderModel.html)

Options for customizing the color and width of the chart border.

### chartArea [`ChartAreaModel`](./api-chartAreaModel.html)

Options for configuring the border and background of the chart area.

### columns `ColumnModel[]`

Options to split chart into multiple plotting areas vertically.
Each object in the collection represents a plotting area in the chart.

### crosshair [`CrosshairSettingsModel`](./api-crosshairSettingsModel.html)

Options for customizing the crosshair of the chart.

### dataSource `Object` &#124;  `DataManager`

Specifies the DataSource for the chart. It can be an array of JSON objects or an instance of DataManager.
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
 dataSource:dataManager,
  series: [{
       xName: 'Id',
       yName: 'Estimate',
       query: query
   }],
...
});
chart.appendTo('#Chart');
```

### description `string`

Description for chart.

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

### enableSideBySidePlacement `boolean`

To enable the side by side placing the points for column type series.

### height `string`

The height of the chart as a string accepts input both as '100px' or '100%'.
If specified as '100%, chart renders to the full height of its parent element.

### indicators `TechnicalIndicatorModel[]`

Defines the collection of technical indicators, that are used in financial markets

### isMultiSelect `boolean`

If set true, enables the multi selection in chart. It requires `selectionMode` to be `Point` | `Series` | or `Cluster`.

### isTransposed `boolean`

It specifies whether the chart should be render in transposed manner or not.

### legendSettings [`LegendSettingsModel`](./api-legendSettingsModel.html)

Options for customizing the legend of the chart.

### locale `string`

Overrides the global culture and localization value for this component. Default global culture is 'en-US'.

### margin [`MarginModel`](./api-marginModel.html)

 Options to customize left, right, top and bottom margins of the chart.

### palettes `string[]`

Palette for the chart series.

### primaryXAxis [`AxisModel`](./api-axisModel.html)

Options to configure the horizontal axis.

### primaryYAxis [`AxisModel`](./api-axisModel.html)

Options to configure the vertical axis.

### rows `RowModel[]`

Options to split Chart into multiple plotting areas horizontally.
Each object in the collection represents a plotting area in the Chart.

### selectedDataIndexes `IndexesModel[]`

Specifies the point indexes to be selected while loading a chart.
It requires `selectionMode` to be `Point` | `Series` | or `Cluster`.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
  selectionMode: 'Point',
  selectedDataIndexes: [ { series: 0, point: 1},
                         { series: 2, point: 3} ],
...
});
chart.appendTo('#Chart');
```

### selectionMode `string`

Specifies whether series or data point has to be selected. They are,
* none: Disables the selection.
* series: selects a series.
* point: selects a point.
* cluster: selects a cluster of point
* dragXY: selects points by dragging with respect to both horizontal and vertical axes
* dragX: selects points by dragging with respect to horizontal axis.
* dragY: selects points by dragging with respect to vertical axis.

### series `SeriesModel[]`

The configuration for series in the chart.

### tabIndex `number`

TabIndex value for the chart.

### theme `string`

Specifies the theme for the chart.

### title `string`

Title of the chart

### titleStyle [`FontModel`](./api-fontModel.html)

Options for customizing the title of the Chart.

### tooltip [`TooltipSettingsModel`](./api-tooltipSettingsModel.html)

Options for customizing the tooltip of the chart.

### useGroupingSeparator `boolean`

Specifies whether a grouping separator should be used for a number.

### width `string`

The width of the chart as a string accepts input as both like '100px' or '100%'.
If specified as '100%, chart renders to the full width of its parent element.

### zoomSettings [`ZoomSettingsModel`](./api-zoomSettingsModel.html)

Options to enable the zooming feature in the chart.
