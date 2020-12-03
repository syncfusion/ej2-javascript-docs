# AccumulationChartModel

Interface for a class AccumulationChart

## Properties

### animationComplete [`EmitType<IAccAnimationCompleteEventArgs>`](./api-iAccAnimationCompleteEventArgs.html)

Triggers after animation gets completed for series.

### annotationRender  `EmitType<IAnnotationRenderEventArgs>`

Triggers before the annotation gets rendered.

### beforePrint  `EmitType<IPrintEventArgs>`

Triggers before the prints gets started.

### chartMouseClick  `EmitType<IMouseEventArgs>`

Triggers on clicking the accumulation chart.

### chartMouseDown  `EmitType<IMouseEventArgs>`

Triggers on mouse down.

### chartMouseLeave  `EmitType<IMouseEventArgs>`

Triggers while cursor leaves the accumulation chart.

### chartMouseMove  `EmitType<IMouseEventArgs>`

Triggers on hovering the accumulation chart.

### chartMouseUp  `EmitType<IMouseEventArgs>`

Triggers on mouse up.

### legendRender  `EmitType<ILegendRenderEventArgs>`

Triggers before the legend gets rendered.

### load [`EmitType<IAccLoadedEventArgs>`](./api-iAccLoadedEventArgs.html)

Triggers before accumulation chart load.

### loaded [`EmitType<IAccLoadedEventArgs>`](./api-iAccLoadedEventArgs.html)

Triggers after accumulation chart loaded.

### pointClick  `EmitType<IPointEventArgs>`

Triggers on point click.

### pointMove  `EmitType<IPointEventArgs>`

Triggers on point move.

### pointRender [`EmitType<IAccPointRenderEventArgs>`](./api-iAccPointRenderEventArgs.html)

Triggers before each points for series gets rendered.

### resized [`EmitType<IAccResizeEventArgs>`](./api-iAccResizeEventArgs.html)

Triggers after window resize.

### seriesRender [`EmitType<IAccSeriesRenderEventArgs>`](./api-iAccSeriesRenderEventArgs.html)

Triggers before the series gets rendered.

### textRender [`EmitType<IAccTextRenderEventArgs>`](./api-iAccTextRenderEventArgs.html)

Triggers before the data label for series gets rendered.

### tooltipRender [`EmitType<IAccTooltipRenderEventArgs>`](./api-iAccTooltipRenderEventArgs.html)

Triggers before the tooltip for series gets rendered.

### annotations `AccumulationAnnotationSettingsModel[]`

The configuration for annotation in chart.

### background `string`

The background color of the chart, which accepts value in hex, rgba as a valid CSS color string.

### border `BorderModel`

Options for customizing the color and width of the chart border.

### dataSource `Object` &#124;  `DataManager`

Specifies the dataSource for the AccumulationChart. It can be an array of JSON objects or an instance of DataManager.
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
    dataSource: dataManager,
    series: [{
       xName: 'Id',
       yName: 'Estimate',
       query: query
   }],
...
});
pie.appendTo('#Pie');
```

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

### enableSmartLabels `boolean`

If set true, labels for the point will be placed smartly without overlapping.

### height `string`

The height of the chart as a string in order to provide input as both like '100px' or '100%'.
If specified as '100%, chart will render to the full height of its parent element.

### isMultiSelect `boolean`

If set true, enables the multi selection in accumulation chart. It requires `selectionMode` to be `Point`.

### legendSettings `LegendSettingsModel`

Options for customizing the legend of accumulation chart.

### locale `string`

Overrides the global culture and localization value for this component. Default global culture is 'en-US'.

### margin `MarginModel`

 Options to customize the left, right, top and bottom margins of accumulation chart.

### selectedDataIndexes `IndexesModel[]`

Specifies the point indexes to be selected while loading a accumulation chart.
It requires `selectionMode` to be `Point`.
```html
<div id='Pie'></div>
```
```typescript
let pie: AccumulationChart = new AccumulationChart({
...
  selectionMode: 'Point',
  selectedDataIndexes: [ { series: 0, point: 1},
                         { series: 2, point: 3} ],
...
});
pie.appendTo('#Pie');
```

### selectionMode `string`

Specifies whether point has to get selected or not. Takes value either 'None 'or 'Point'

### series `AccumulationSeriesModel[]`

The configuration for series in accumulation chart.

### theme `string`

Specifies the theme for accumulation chart.

### title `string`

Title for accumulation chart

### titleStyle `FontModel`

Options for customizing the `title` of accumulation chart.

### tooltip `TooltipSettingsModel`

Options for customizing the tooltip of accumulation chart.

### width `string`

The width of the chart as a string in order to provide input as both like '100px' or '100%'.
If specified as '100%, chart will render to the full width of its parent element.
