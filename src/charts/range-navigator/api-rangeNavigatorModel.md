# RangeNavigatorModel

Interface for a class RangeNavigator

## Properties

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

### allowSnapping `boolean`

Enable snapping for range navigator sliders

### animationDuration `number`

Duration of the animation

### dataSource `Object` &#124;  `DataManager`

It defines the data source for a range navigator.

### disableRangeSelector `boolean`

To render the period selector with out range navigator.

### enableDeferredUpdate `boolean`

Enable deferred update for the range navigator

### enableGrouping `boolean`

Enable grouping for the labels

### enablePersistence `boolean`

Enable or disable persisting component's state between page reloads.

### enableRtl `boolean`

Enable or disable rendering component in right to left direction.

### groupBy `string`

GroupBy property for the axis

### height `string`

The height of the chart as a string accepts input both as '100px' or '100%'.
If specified as '100%, range navigator renders to the full height of its parent element.

### interval `number`

interval value for the axis

### intervalType `string`

IntervalType for the dateTime axis

### labelFormat `string`

Used to format the axis label that accepts any global string format like 'C', 'n1', 'P' etc.
It also accepts placeholder like '{value}°C' in which value represent the axis label, e.g, 20°C.

### labelIntersectAction `string`

Specifies, when the axis labels intersect with each other.They are,
* None: Shows all the labels.
* Hide: Hides the label when it intersects.

### labelPosition `string`

Label positions for the axis

### labelStyle `FontModel`

Label style for the labels

### locale `string`

Overrides the global culture and localization value for this component. Default global culture is 'en-US'.

### logBase `number`

base value for log axis

### majorGridLines `MajorGridLinesModel`

MajorGridLines

### majorTickLines `MajorTickLinesModel`

MajorTickLines

### margin `MarginModel`

Margin for the range navigator

### maximum `number` &#124;  `Date`

Maximum value for the axis

### minimum `number` &#124;  `Date`

Minimum value for the axis

### navigatorBorder `BorderModel`

Options for customizing the color and width of the chart border.

### navigatorStyleSettings [`StyleSettingsModel`](./api-styleSettingsModel.html)

Navigator style settings

### periodSelectorSettings [`PeriodSelectorSettingsModel`](./api-periodSelectorSettingsModel.html)

Period selector settings

### query `Query`

It defines the query for the data source.

### secondaryLabelAlignment `string`

It specifies the label alignment for secondary axis labels

### series `RangeNavigatorSeriesModel[]`

It defines the configuration of series in the range navigator

### skeleton `string`

Specifies the skeleton format in which the dateTime format will process.

### skeletonType `string`

It specifies the type of format to be used in dateTime format process.

### theme `string`

Specifies the theme for the range navigator.

### tickPosition `string`

Tick Position for the axis

### tooltip [`RangeTooltipSettingsModel`](./api-rangeTooltipSettingsModel.html)

Options for customizing the tooltip of the chart.

### useGroupingSeparator `boolean`

Specifies whether a grouping separator should be used for a number.

### value `number[]` &#124;  `Date[]`

Selected range for range navigator.

### valueType `string`

ValueType for the axis

### width `string`

The width of the range navigator as a string accepts input as both like '100px' or '100%'.
If specified as '100%, range navigator renders to the full width of its parent element.

### xName `string`

It defines the xName for the range navigator.

### yName `string`

It defines the yName for the range navigator.
