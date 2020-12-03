# ZoomSettings

Configures the zooming behavior for the chart.

## Properties

### enableDeferredZooming `boolean`

If set to true, zooming will be performed on mouse up. It requires `enableSelectionZooming` to be true.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
   zoomSettings: {
     enableSelectionZooming: true,
     enableDeferredZooming: false
   }
...
});
chart.appendTo('#Chart');
```

Defaults to *true*

### enableMouseWheelZooming `boolean`

If set to true, chart can be zoomed by using mouse wheel.

Defaults to *false*

### enablePan `boolean`

Specifies whether chart needs to be panned by default.

Defaults to *false.*

### enablePinchZooming `boolean`

If to true, chart can be pinched to zoom in / zoom out.

Defaults to *false*

### enableScrollbar `boolean`

Specifies whether axis needs to have scrollbar.

Defaults to *false.*

### enableSelectionZooming `boolean`

If set to true, chart can be zoomed by a rectangular selecting region on the plot area.

Defaults to *false*

### mode `string`

Specifies whether to allow zooming vertically or horizontally or in both ways. They are,
* x,y: Chart can be zoomed both vertically and horizontally.
* x: Chart can be zoomed horizontally.
* y: Chart can be zoomed  vertically.
 It requires `enableSelectionZooming` to be true.
```html
<div id='Chart'></div>
```
```typescript
let chart: Chart = new Chart({
...
   zoomSettings: {
     enableSelectionZooming: true,
     mode: 'XY'
   }
...
});
chart.appendTo('#Chart');
```

Defaults to *'XY'*

### toolbarItems `ToolbarItems[]`

Specifies the toolkit options for the zooming as follows:
* Zoom
* ZoomIn
* ZoomOut
* Pan
* Reset

Defaults to *'["Zoom", "ZoomIn", "ZoomOut", "Pan", "Reset"]'*
