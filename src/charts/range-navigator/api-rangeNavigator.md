# RangeNavigator

Range Navigator

## Properties

### allowSnapping `boolean`

Enable snapping for range navigator sliders

Defaults to *false*

### animationDuration `number`

Duration of the animation

Defaults to *500*

### areaSeriesModule `AreaSeries`

`areaSeriesModule` is used to add area series in the chart.

### dataSource `Object` &#124;  `DataManager`

It defines the data source for a range navigator.

Defaults to *null*

### dateTimeModule `DateTime`

`datetimeModule` is used to manipulate and add dateTime axis to the chart.

### disableRangeSelector `boolean`

To render the period selector with out range navigator.

Defaults to *false*

### doubleModule `Double`

`doubleModule` is used to manipulate and add double axis to the chart.

### enableDeferredUpdate `boolean`

Enable deferred update for the range navigator

Defaults to *false*

### enableGrouping `boolean`

Enable grouping for the labels

Defaults to *false*

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

Defaults to *false*

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

Defaults to *false*

### groupBy `string`

GroupBy property for the axis

Defaults to *`Auto`*

### height `string`

The height of the chart as a string accepts input both as '100px' or '100%'.
If specified as '100%, range navigator renders to the full height of its parent element.

Defaults to *null*

### interval `number`

interval value for the axis

Defaults to *null*

### intervalType `string`

IntervalType for the dateTime axis

Defaults to *'Auto'*

### labelFormat `string`

Used to format the axis label that accepts any global string format like 'C', 'n1', 'P' etc.
It also accepts placeholder like '{value}°C' in which value represent the axis label, e.g, 20°C.

Defaults to *''*

### labelIntersectAction `string`

Specifies, when the axis labels intersect with each other.They are,
* None: Shows all the labels.
* Hide: Hides the label when it intersects.

Defaults to *Hide*

### labelPosition `string`

Label positions for the axis

Defaults to *'Outside'*

### labelStyle `FontModel`

Label style for the labels

### lineSeriesModule `LineSeries`

`lineSeriesModule` is used to add line series to the chart.

### locale `string`

Overrides the global culture and localization value for this component. Default global culture is 'en-US'.

Defaults to *undefined*

### logBase `number`

base value for log axis

Defaults to *10*

### logarithmicModule `Logarithmic`

`logarithmicModule` is used to manipulate and add log axis to the chart.

### majorGridLines `MajorGridLinesModel`

MajorGridLines

### majorTickLines `MajorTickLinesModel`

MajorTickLines

### margin `MarginModel`

Margin for the range navigator

### maximum `number` &#124;  `Date`

Maximum value for the axis

Defaults to *null*

### minimum `number` &#124;  `Date`

Minimum value for the axis

Defaults to *null*

### navigatorBorder `BorderModel`

Options for customizing the color and width of the chart border.

### navigatorStyleSettings [`StyleSettingsModel`](./api-styleSettingsModel.html)

Navigator style settings

### periodSelectorModule [`PeriodSelector`](./api-periodSelector.html)

`periodSelectorModule` is used to add period selector un range navigator

### periodSelectorSettings [`PeriodSelectorSettingsModel`](./api-periodSelectorSettingsModel.html)

Period selector settings

### query `Query`

It defines the query for the data source.

Defaults to *null*

### rangeTooltipModule [`RangeTooltip`](./api-rangeTooltip.html)

`tooltipModule` is used to manipulate and add tooltip to the series.

### secondaryLabelAlignment `string`

It specifies the label alignment for secondary axis labels

Defaults to *'Middle'*

### series `RangeNavigatorSeriesModel[]`

It defines the configuration of series in the range navigator

### skeleton `string`

Specifies the skeleton format in which the dateTime format will process.

Defaults to *''*

### skeletonType `string`

It specifies the type of format to be used in dateTime format process.

Defaults to *'DateTime'*

### stepLineSeriesModule `StepLineSeries`

`stepLineSeriesModule` is used to add stepLine series in the chart.

### theme `string`

Specifies the theme for the range navigator.

Defaults to *'Material'*

### tickPosition `string`

Tick Position for the axis

Defaults to *'Outside'*

### tooltip [`RangeTooltipSettingsModel`](./api-rangeTooltipSettingsModel.html)

Options for customizing the tooltip of the chart.

### useGroupingSeparator `boolean`

Specifies whether a grouping separator should be used for a number.

Defaults to *false*

### value `number[]` &#124;  `Date[]`

Selected range for range navigator.

Defaults to *[]*

### valueType `string`

ValueType for the axis

Defaults to *'Double'*

### width `string`

The width of the range navigator as a string accepts input as both like '100px' or '100%'.
If specified as '100%, range navigator renders to the full width of its parent element.

Defaults to *null*

### xName `string`

It defines the xName for the range navigator.

Defaults to *null*

### yName `string`

It defines the yName for the range navigator.

Defaults to *null*

## Methods

### addEventListener

Adds the handler to the given event listener.

Returns *void*

### appendTo

Appends the control within the given HTML element

| Parameter | Type | Description |
|------|------|-------------|
| selector (*optional*) |  `string` &#124;  `HTMLElement` | Target element where control needs to be appended<br> |

Returns *void*

### createSecondaryElement

Creating secondary range navigator

Returns *void*

### dataBind

When invoked, applies the pending property changes immediately to the component.

Returns *void*

### destroy

To destroy the widget

Returns *void*

### export

Handles the export method for range navigator control.

Returns *void*

### getModuleName

To get the module name of the widget

Returns *string*

### onPropertyChanged

OnProperty change method calling here

Returns *void*

### preRender

Starting point of the control initialization

Returns *void*

### print

Handles the print method for range navigator control.

Returns *void*

### refresh

Applies all the pending property changes and render the component again.

Returns *void*

### removeEventListener

Removes the handler from the given event listener.

Returns *void*

### render

To render the range navigator

Returns *void*

### renderChart

Creating Chart for range navigator

Returns *void*

### Inject

Dynamically injects the required modules to the component.

Returns *void*

## Events

### beforePrint  `EmitType<IPrintEventArgs>`

Triggers before the prints gets started.

### changed [`EmitType<IChangedEventArgs>`](./api-iChangedEventArgs.html)

Triggers after change the slider.

### labelRender [`EmitType<ILabelRenderEventsArgs>`](./api-iLabelRenderEventsArgs.html)

Triggers before the label rendering

### load [`EmitType<IRangeLoadedEventArgs>`](./api-iRangeLoadedEventArgs.html)

Triggers before the range navigator rendering

### loaded [`EmitType<IRangeLoadedEventArgs>`](./api-iRangeLoadedEventArgs.html)

Triggers after the range navigator rendering

### resized  `EmitType<IResizeRangeNavigatorEventArgs>`

Triggers after the range navigator resized

### selectorRender [`EmitType<IRangeSelectorRenderEventArgs>`](./api-iRangeSelectorRenderEventArgs.html)

Triggers before the range navigator selector rendering

### tooltipRender [`EmitType<IRangeTooltipRenderEventArgs>`](./api-iRangeTooltipRenderEventArgs.html)

Triggers before the tooltip for series is rendered.
