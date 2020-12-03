---
title: " Chart API Migration | TypeScript "

component: "Chart"

description: "This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2."
---

# Migration from Essential JS 1

This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2.

## Annotations

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>rotation of annotation</b></td>
<td>
<b>Property</b>:<i>annotations.angle</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{angle: 90}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.rotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ rotation: 90}];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>annotations</b></td>
<td>
<b>Property</b>:<i>annotations.content</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{ content: '<div>Chart</div>'}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.content</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ content: '<div>Chart</div>'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>coordinate unit for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.coordinateUnit</i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ coordinateUnit :"pixels"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.coordinateUnits</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ coordinateUnits: 'Pixel'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>horizontalAlignment for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.horizontalAlignment </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ horizontalAlignment :"middle"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.horizontalAlignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ horizontalAlignment: 'Center'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>margin for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.margin </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ margin { right: 5, left: 5, top: 5, bottom: 5}}]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Opacity for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.opacity </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ opacity: 0.4 }]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>Region for annotation with respect to chart or series</b></td>
<td>
<b>Property</b>:<i>annotations.region </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ region :"chart"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.region</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ region: 'Chart'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>verticalAlignment for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.verticalAlignment </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ verticalAlignment :"middle"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.verticalAlignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ verticalAlignment: 'Center'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Visibility of annotations</b></td>
<td>
<b>Property</b>:<i>annotations.visible </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ visible: true }]
});
</code>
</td>
<td>
<b>Not applicable</b>
</td>
</tr>

<tr>
<td><b>X offset for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.x </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ x :"100"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.x</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ x: '100'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>X axis name in which annotation to be rendered</b></td>
<td>
<b>Property</b>:<i>annotations.xAxisName </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ xAxisName :"xAxis"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.xAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ xAxisName: 'xAxis'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Y offset for annotation</b></td>
<td>
<b>Property</b>:<i>annotations.y</i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ y :"100"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.y</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ y: '100'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Y axis name in which annotation to be rendered</b></td>
<td>
<b>Property</b>:<i>annotations.yAxisName </i>
</br>
</br>
<code>
$("#container").ejChart({
   annotations :[{ xAxisName :"yAxis"}]
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations.yAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
annotations: [{ xAxisName: 'yAxis'}]
});
chart.appendTo('#chart');
</code></td>
</tr>

</table>

## Columns

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Columns in chart</b></td>
<td>
<b>Property</b>:<i>columnDefinitions</i>
</br>
</br>
<code>
$("#chart").ejChart({
    columnDefinitions: [];
});
</code>
</td>
<td>
<b>Property</b>:<i>columns</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    columns: [];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>unit</b></td>
<td>
<b>Property</b>:<i>unit </i>
</br>
</br>
<code>
$("#container").ejChart({
   columnDefinitions :[{unit : "percentage"}]
});
</code>
</td>
<td>
<b>Not Applicable</b>
</td>
</tr>

<tr>
<td><b>width of columns in chart</b></td>
<td>
<b>Property</b>:<i>columnWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    columnDefinitions: [{ columnWidth: '50%'}];
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    columns: [ { width: '300'}];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Line customization</b></td>
<td>
<b>Property</b>:<i>lineColor, lineWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    columnDefinitions: [{ columnWidth: '50%', lineColor: 'brown', lineWidth: 2}];
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    columns: [ { width: '300', border: { width: 2, color: 'brown'}}];
});
chart.appendTo('#chart');
</code></td>
</tr>
</table>

## CommonSeriesOptions

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>commonSeriesOptios</b></td>
<td>
<b>Property</b>:<i>commonSeriesOptions </i>
</br>
</br>
<code>
$("#container").ejChart({
   commonSeriesOptions: { }
});
</code>
</td>
<td>
<b>Not Applicable</b>
</td>
</tr>

</table>

## Crosshair

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>crosshair</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   crosshair: { visible: true}
});
</code>
</td>
<td>
<b>Property</b>:<i>enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    crosshair: { enable: false }
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>trackballTooltipSettings</b></td>
<td>
<b>Property</b>:<i>trackballTooltipSettings</i>
</br>
</br>
<code>
$("#container").ejChart({
   crosshair : { trackballTooltipSettings : { border : { width :2 } } }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>marker</b></td>
<td>
<b>Property</b>:<i>marker</i>
</br>
</br>
<code>
$("#container").ejChart({
   crosshair : { marker : { border : { width :2 } } }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>crosshair line style</b></td>
<td>
<b>Property</b>:<i>line</i>
</br>
</br>
<code>
$("#container").ejChart({
   crosshair : { line: { width: 2, color: 'red' } }
});
</code>
</td>
<td>
let chart: Chart = new Chart({
    crosshair: { border: { width: 2, color: 'black' }}
});
</td>
</tr>

<tr>
<td><b>type</b></td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
$("#container").ejChart({
   crosshair : {  type: 'trackball' }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

## 3D chart

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>3d chart</b></td>
<td>
<b>Property</b>:<i>enable3D</i>
</br>
</br>
<code>
$("#container").ejChart({
   enable3D: true
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Rotation of 3d chart</b></td>
<td>
<b>Property</b>:<i>enableRotation</i>
</br>
</br>
<code>
$("#container").ejChart({
   enableRotation: false
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>depth</b></td>
<td>
<b>Property</b>:<i>depth</i>
</br>
</br>
<code>
$("#container").ejChart({
   depth: 45
});
</code>
</td>
<td>
Not applicable
</td>
</tr>
</table>

## Canvas rendering

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>canvas rendering</b></td>
<td>
<b>Property</b>:<i>enableCanvasRendering</i>
</br>
</br>
<code>
$("#container").ejChart({
   enableCanvasRendering: true
});
</code>
</td>
<td>
Not applicable
</td>
</tr>
</table>

## Indicators

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Type of Indicator</b></td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { type: 'Sma' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { type: 'Sma' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Period for indicator</b></td>
<td>
<b>Property</b>:<i>period</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { period: 14 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { period: 14 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Period for indicator</b></td>
<td>
<b>Property</b>:<i>period</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { period: 14 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>period</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { period: 14 }]
});
</code>
</td>
</tr>

<tr>
<td><b>%K value in stochastic indicator</b></td>
<td>
<b>Property</b>:<i>kPeriod</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { kPeriod: 14 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>kPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { kPeriod: 14 }]
});
</code>
</td>
</tr>

<tr>
<td><b>%D value in stochastic indicator</b></td>
<td>
<b>Property</b>:<i>dPeriod</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { dPeriod: 3 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>dPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { dPeriod: 3 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Shows overSold/overBought values</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>showZones</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { showZones: true }]
});
</code>
</td>
</tr>

<tr>
<td><b>Overbought value for RSI and stochastic indicator</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>overBought</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { overBought: 80 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Oversold value for RSI and stochastic indicator</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>overSold</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { overSold: 20 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Standard deviation for Bollingerbands</b></td>
<td>
<b>Property</b>:<i>standardDeviations</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { standardDeviations: 2 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>standardDeviation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { standardDeviation: 2 }]
});
</code>
</td>
</tr>

<tr>
<td><b>standard deviation</b></td>
<td>
<b>Property</b>:<i>standardDeviations</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { standardDeviations: 2 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>standardDeviation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { standardDeviation: 2 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Field for indicator</b></td>
<td>
<b>Property</b>:<i>field</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { field: 'Close' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>field</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { field: 'Close' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Slow period for MACD indicator</b></td>
<td>
<b>Property</b>:<i>shortPeriod</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { shortPeriod: 12 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>slowPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { slowPeriod: 12 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Fast period for MACD indicator</b></td>
<td>
<b>Property</b>:<i>longPeriod</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { longPeriod: 26 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>fastPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { fastPeriod: 26 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Line style for MACD indicator</b></td>
<td>
<b>Property</b>:<i>macdLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { macdLine: { width: 2, fill: 'red' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>fastPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { macdLine: { width: 2, color: 'red' } }]
});
</code>
</td>
</tr>

<tr>
<td><b>Type of MACD indicator</b></td>
<td>
<b>Property</b>:<i>macdType</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { macdType: 'both' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>fastPeriod</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { macdType: 'Both' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Color of the positive bars in Macd indicators</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>macdPositiveColor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { macdPositiveColor: 'red' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Color of the negative bars in Macd indicators</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>macdNegativeColor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { macdNegativeColor: 'red' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Color for Bollinger bands</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>bandColor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    indicators: [ { bandColor: 'red' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Appearance of upper line in indicator</b></td>
<td>
<b>Property</b>:<i>upperLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { upperLine: { fill: '#EECCAA', width: 2 } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>upperLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { upperLine: {  type: 'Smooth', color: '#FFEEFF', width: 2, dashArray: '10,5' } }]
});
</code>
</td>
</tr>

<tr>
<td><b>Appearance of lower line in indicator</b></td>
<td>
<b>Property</b>:<i>lowerLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { lowerLine: { fill: '#EECCAA', width: 2 } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lowerLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { lowerLine: {  type: 'Smooth', color: '#FFEEFF', width: 2, dashArray: '10,5' } }]
});
</code>
</td>
</tr>

<tr>
<td><b>Appearance of period line in indicator</b></td>
<td>
<b>Property</b>:<i>periodLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { periodLine: { fill: '#EECCAA', width: 2 } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lowerLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { lowerLine: {  type: 'Smooth', color: '#FFEEFF', width: 2, dashArray: '10,5' } }]
});
</code>
</td>
</tr>

<tr>
<td><b>Name of the series for which indicator has to be drawn.</b></td>
<td>
<b>Property</b>:<i>seriesName</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { seriesName: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lowerLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     indicators: [ { seriesName: '' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Options to customize the histogram in MACD indicator</b></td>
<td>
<b>Property</b>:<i>seriesName</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { histogram: { } }]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Enabling animation</b></td>
<td>
<b>Property</b>:<i>enableAnimation</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { enableAnimation: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { animation: { enable: true }]
});
</code>
</td>
</tr>

<tr>
<td><b>Animation duration</b></td>
<td>
<b>Property</b>:<i>animationDuration</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { animationDuration: 3000 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.duration</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { animation: { duration: 3000 }]
});
</code>
</td>
</tr>

<tr>
<td><b>Tooltip</b></td>
<td>
<b>Property</b>:<i>tooltip</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { tooltip: { visible: true } }]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Trigger value of MACD indicator.</b></td>
<td>
<b>Property</b>:<i>trigger</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { trigger: 14 }]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fill color for indicator</b></td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { fill: '#EEDDCC' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { fill: 'red' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Width for indicator</b></td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { width: 2 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { width: 3 }]
});
</code>
</td>
</tr>

<tr>
<td><b>xAxis Name of  indicator</b></td>
<td>
<b>Property</b>:<i>xAxisName</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { xAxisName: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>xAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { xAxisName: '' }]
});
</code>
</td>
</tr>

<tr>
<td><b>yAxis Name of  indicator</b></td>
<td>
<b>Property</b>:<i>yAxisName</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { yAxisName: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>yAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
   indicators: [ { yAxisName: '' }]
});
</code>
</td>
</tr>

<tr>
<td><b>Visibility of indicator</b></td>
<td>
<b>Property</b>:<i>visibility</i>
</br>
</br>
<code>
$("#container").ejChart({
   indicators: [ { visibility: true }]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

</table>

## Legend

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Default legend</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { visible: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { visible: true }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend height</b></td>
<td>
<b>Property</b>:<i>size.height</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { size : { height: 50 }  }
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { height: '30' }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend width</b></td>
<td>
<b>Property</b>:<i>size.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { size: { width: 20 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { width: '30' }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend location in chart</b></td>
<td>
<b>Property</b>:<i>location</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { location: { x: 3, y: 45} }
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { location: { x: 3, y: 45} }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend position in chart</b></td>
<td>
<b>Property</b>:<i>position</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { position: 'top' }
});
</code>
</td>
<td>
<b>Property</b>:<i>position</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { position: 'Top' }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend padding</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>padding</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { padding: 8 }
});
</code>
</td>
</tr>

<tr>
<td><b>Legend alignment</b></td>
<td>
<b>Property</b>:<i>position</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { alignment: 'center' }
});
</code>
</td>
<td>
<b>Property</b>:<i>position</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { alignment: 'Center' }
});
</code>
</td>
</tr>

<tr>
<td><b>text style for legend</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { font: { fontFamily: '', fontWeight: '400', fontStyle: 'italic', size: '12px' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>textStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { textStyle: { size: '12px' , color: 'red', fontFamily: 'Italic', fontWeight: '400', fontStyle: 'Normal', opacity: 1, textAlignment: 'Center', textOverFlow: 'Trim'} }
});
</code>
</td>
</tr>

<tr>
<td><b>shape height of legend</b></td>
<td>
<b>Property</b>:<i>itemStyle.height</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { itemStyle: { height: 20 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>shapeHeight</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { shapeHeight: 20 }
});
</code>
</td>
</tr>

<tr>
<td><b>shape width of legend</b></td>
<td>
<b>Property</b>:<i>itemStyle.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { itemStyle: { width: 20 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>shapeWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { shapeWidth: 20 }
});
</code>
</td>
</tr>

<tr>
<td><b>shape width of legend</b></td>
<td>
<b>Property</b>:<i>itemStyle.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { itemStyle: { width: 20 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>shapeWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { shapeWidth: 20 }
});
</code>
</td>
</tr>
<tr>
<td><b>shape border of legend</b></td>
<td>
<b>Property</b>:<i>itemStyle.border</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { itemStyle: { border: { width: 2, color: 'red' } } }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>shape padding of legend</b></td>
<td>
<b>Property</b>:<i>itemPadding</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { itemPadding: 10 }
});
</code>
</td>
<td>
<b>Property</b>:<i>shapePadding</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { shapePadding: 20 }
});
</code>
</td>
</tr>

<tr>
<td><b>Background of legend</b></td>
<td>
<b>Property</b>:<i>background</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { background: 'transparent' }
});
</code>
</td>
<td>
<b>Property</b>:<i>backgorund</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { background: 'transparent' }
});
</code>
</td>
</tr>

<tr>
<td><b>Opacity of legend</b></td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { opacity: 0.3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { opacity: 0.4 }
});
</code>
</td>
</tr>

<tr>
<td><b>Toggle visibility of series while legend click</b></td>
<td>
<b>Property</b>:<i>toggleSeriesVisibility</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { toggleSeriesVisibility: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>toggleVisibility</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: { toggleVisibility: true }
});
</code>
</td>
</tr>

<tr>
<td><b>Title for legend</b></td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { title: { text: 'LegendTitle', font: { }, textAlignment: 'middle' } }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Text Overflow for legend</b></td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { textOverFlow: 'trim' }
});
</code>
</td>
<td>
<b>Property</b>:<i>textStyle.textOverFlow</i>
</br>
</br>
<code>
let chart: new Chart({
   legend: { text: { textOverFlow: 'trim' } }
});
</code>
</td>
</tr>

<tr>
<td><b>Text width for legend while setting text overflow</b></td>
<td>
<b>Property</b>:<i>textWidth</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { textWidth: 20 }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Scroll bar for legend</b></td>
<td>
<b>Property</b>:<i>enableScrollBar</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { enableScrollBar: true }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Row count for legend</b></td>
<td>
<b>Property</b>:<i>rowCount</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { rowCount: 2 }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Column count for legend</b></td>
<td>
<b>Property</b>:<i>columnCount</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { columnCount: 2 }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Color for legend items</b></td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
$("#container").ejChart({
   legend: { fill: '#EEFFCC' }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

</table>

## primaryXAxis

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Alternate grid band</b></td>
<td>
<b>Property</b>:<i>alternateGridBand </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { alternateGridBand: {  even: { fill: 'red }}}
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Axis line cross value</b></td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { crossesAt: 0 }
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { crossesAt: 4}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis name with which the axis line has to be crossed</b></td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { crossesInAxis: '' }
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { crossesInAxis: '' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis elements placed with axis line</b></td>
<td>
<b>Property</b>:<i>showNextToAxisLine </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { showNextToAxisLine : true }
});
</code>
</td>
<td>
<b>Property</b>:<i>placeNextToAxisLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { placeNextToAxisLine: '' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line style</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { axisLine: { color : 'red' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { lineStyle: { color: 'black' } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line dashArray</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { axisLine: { dashArray : '10, 5' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { lineStyle: { dashArray: '10, 5' } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Offset for axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { axisLine: { offset : 10 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { plotOffset: 10 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Visible of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { axisLine: { visible :  false } }
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { visible: false }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Width of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { axisLine: { width :  2 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { lineStyle: { width: 3 } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Column index of an axis</b></td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { columnIndex: 2 }
});
</code>
</td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { columnIndex: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>span of an axis to place horizontally or vertically</b></td>
<td>
<b>Property</b>:<i>columnSpan</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { columnIndex: 2 }
});
</code>
</td>
<td>
<b>Property</b>:<i>span</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { span: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label of an axis</b></td>
<td>
<b>Property</b>:<i>crossHairLabel.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { crossHairLabel: { visible: true }}
});
</code>
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { crossHairTooltip: { enable: true }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label color of an axis</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { crossHairTooltip: { fill: 'red' }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label text style</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.textStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { crossHairTooltip: { textStyle: { } }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Desired interval count for primaryXAxis</b></td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { desiredIntervals: 4}
});
</code>
</td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { desiredIntervals: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Edges primaryXAxis</b></td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { edgeLabelPlacement: 'none' }
});
</code>
</td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { edgeLabelPlacement: 'Shift'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Enables trim for axis labels</b></td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { enableTrim: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { enableTrim: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { enableAutoIntervalOnZooming: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { enableAutoIntervalOnZooming: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { enableAutoIntervalOnZooming: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { enableAutoIntervalOnZooming: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Font style for primaryXAxis</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { font: { fontFamily: 'Calibri', fontStyle: 'italic', fontWeight: '', opacity: 0.5, size: 12} }
});
</code>
</td>
<td>
<b>Property</b>:<i>titleStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { titleStyle: { }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Indexed for category axis</b></td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { isIndexed: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { isIndexed: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Interval type for date time axis</b></td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { intervalType}: 'Auto' }
});
</code>
</td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { intervalType: 'Auto  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Inversed axis</b></td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { isInversed: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { isInversed: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Custom label format</b></td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelFormat: '{value}K' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelFormat: '{value}K'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelIntersectAction</b></td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelIntersectAction: 'trim' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelIntersectAction: 'Trim'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPosition</b></td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelPosition: 'inside' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelPosition: 'Inside'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPlacement for category axis</b></td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelPlacement: 'onTicks' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelPlacement: 'OnTicks'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Axis label alignment</b></td>
<td>
<b>Property</b>:<i>alignment</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { alignment: 'center' }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Rotation of axis labels</b></td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelRotation: 45 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelRotation: 45  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Log base value for logarithmic axis</b></td>
<td>
<b>Property</b>:<i>logBase</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { logBase: 10 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { logBase: 10  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorGridLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorGridLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorGridLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorGridLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorGridLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorGridLines: { dashArray: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorGridLines: { dashArray: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorGridLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorTickLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorTickLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorTickLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorTickLines: { size: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorTickLines: { height: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorTickLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { majorTickLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { majorTickLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>maximum labels of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { maximumLabels: 5 }
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { maximumLabels: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum labels width of primaryXAxis to trim</b></td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { maximumLabelWidth: 40 }
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { maximumLabelWidth: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorGridLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorGridLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorGridLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorGridLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorGridLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorGridLines: { dashArray: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorGridLines: { dashArray: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorGridLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTickLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTickLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorTickLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTickLines: { size: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorTickLines: { height: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTickLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorTickLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTickLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Minor ticks per interval of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>minorTicksPerInterval</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { minorTicksPerInterval: 4 }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minorTicksPerInterval: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>name of the primaryXAxis</b></td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { name: 'primaryXAxis' }
});
</code>
</td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { name: 'primaryXAxis' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Orientation of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>orientation</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { orientation: 'Vertical' }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Plot offset for primaryXAxis</b></td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { plotOffset: 0 }
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { plotOffset: 0 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minimum for  primaryXAxis</b></td>
<td>
<b>Property</b>:<i>range.minimum</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { range: { minimum: 10 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>minimum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { minimum: 23 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum for primaryXAxis</b></td>
<td>
<b>Property</b>:<i>range.maximum</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { range: { maximum: 10 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>maximum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { maximum: 23 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>interval for  primaryXAxis</b></td>
<td>
<b>Property</b>:<i>range.interval</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { range: { interval: 1 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>interval</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { interval: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>RangePadding for  primaryXAxis</b></td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { rangePadding: 'None' }}
});
</code>
</td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { rangePadding: 'None' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Rounding Places in primaryXAxis</b></td>
<td>
<b>Property</b>:<i>roundingPlaces </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { roundingPlaces: 3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { labelFormat: 'n3' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>ScrollBar settings of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>scrollbarSettings </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { scrollbarSettings : { } }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>TickPosition in primaryXAxis</b></td>
<td>
<b>Property</b>:<i>tickLinesPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { tickLinesPosition: 'Inside' }
});
</code>
</td>
<td>
<b>Property</b>:<i>tickPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { tickPosition: 'Inside' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>valueType of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { valueType: 'DateTime' }
});
</code>
</td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { valueType: 'DateTime' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>visible of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { visible: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { visible: true }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomFactor of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { zoomFactor: 0.3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { zoomFactor: 0.3 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomPosition of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { zoomPosition: 0.3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { zoomPosition: 0.3 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelBorder of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>labelBorder</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { labelBorder: { color: 'red', width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { border: { color: 'red', width: 3 } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>title of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>title.text</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { title: { text: 'Chart title' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { title: 'Chart title' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>StripLine of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>stripLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { stripLine: [] }
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [] }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Multilevel labels of primaryXAxis</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryXAxis: { multiLevelLabels: [] }
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [] }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>skeleton for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeleton</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeleton: 'yMd' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>
<tr>
<td><b>skeleton type for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeletonType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeletonType: 'DateTime' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<table>

## primaryYAxis

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Alternate grid band</b></td>
<td>
<b>Property</b>:<i>alternateGridBand </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { alternateGridBand: {  even: { fill: 'red }}}
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Axis line cross value</b></td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { crossesAt: 0 }
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { crossesAt: 4}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis name with which the axis line has to be crossed</b></td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { crossesInAxis: '' }
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { crossesInAxis: '' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis elements placed with axis line</b></td>
<td>
<b>Property</b>:<i>showNextToAxisLine </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { showNextToAxisLine : true }
});
</code>
</td>
<td>
<b>Property</b>:<i>placeNextToAxisLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { placeNextToAxisLine: '' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line style</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { axisLine: { color : 'red' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { lineStyle: { color: 'black' } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line dashArray</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { axisLine: { dashArray : '10, 5' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { lineStyle: { dashArray: '10, 5' } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Offset for axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { axisLine: { offset : 10 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { plotOffset: 10 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Visible of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { axisLine: { visible :  false } }
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { visible: false }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Width of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { axisLine: { width :  2 } }
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { lineStyle: { width: 3 } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Column index of an axis</b></td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { columnIndex: 2 }
});
</code>
</td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { columnIndex: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>span of an axis to place horizontally or vertically</b></td>
<td>
<b>Property</b>:<i>columnSpan</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { columnIndex: 2 }
});
</code>
</td>
<td>
<b>Property</b>:<i>span</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { span: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label of an axis</b></td>
<td>
<b>Property</b>:<i>crossHairLabel.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { crossHairLabel: { visible: true }}
});
</code>
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { crossHairTooltip: { enable: true }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label color of an axis</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { crossHairTooltip: { fill: 'red' }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label text style</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.textStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { crossHairTooltip: { textStyle: { } }}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Desired interval count for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { desiredIntervals: 4}
});
</code>
</td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { desiredIntervals: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Edges primaryYAxis</b></td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { edgeLabelPlacement: 'none' }
});
</code>
</td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { edgeLabelPlacement: 'Shift'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Enables trim for axis labels</b></td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { enableTrim: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { enableTrim: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { enableAutoIntervalOnZooming: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { enableAutoIntervalOnZooming: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { enableAutoIntervalOnZooming: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { enableAutoIntervalOnZooming: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Font style for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { font: { fontFamily: 'Calibri', fontStyle: 'italic', fontWeight: '', opacity: 0.5, size: 12} }
});
</code>
</td>
<td>
<b>Property</b>:<i>titleStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { titleStyle: { }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Indexed for category axis</b></td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { isIndexed: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { isIndexed: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Interval type for date time axis</b></td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { intervalType}: 'Auto' }
});
</code>
</td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { intervalType: 'Auto  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Inversed axis</b></td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { isInversed: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { isInversed: true  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Custom label format</b></td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelFormat: '{value}K' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelFormat: '{value}K'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelIntersectAction</b></td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelIntersectAction: 'trim' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelIntersectAction: 'Trim'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPosition</b></td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelPosition: 'inside' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelPosition: 'Inside'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPlacement for category axis</b></td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelPlacement: 'onTicks' }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelPlacement: 'OnTicks'  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Axis label alignment</b></td>
<td>
<b>Property</b>:<i>alignment</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { alignment: 'center' }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Rotation of axis labels</b></td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelRotation: 45 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelRotation: 45  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Log base value for logarithmic axis</b></td>
<td>
<b>Property</b>:<i>logBase</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { logBase: 10 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { logBase: 10  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorGridLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorGridLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorGridLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorGridLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorGridLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorGridLines: { dashArray: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorGridLines: { dashArray: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorGridLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorTickLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorTickLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorTickLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorTickLines: { size: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorTickLines: { height: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorTickLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { majorTickLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { majorTickLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>maximum labels of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { maximumLabels: 5 }
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { maximumLabels: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum labels width of primaryYAxis to trim</b></td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { maximumLabelWidth: 40 }
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { maximumLabelWidth: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorGridLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorGridLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorGridLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorGridLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorGridLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorGridLines: { dashArray: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorGridLines: { dashArray: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorGridLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTickLines: { visible: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTickLines: { width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorTickLines: { width: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTickLines: { size: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorTickLines: { height: 2}  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTickLines: { color: 'black' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorTickLines: { color: 'black'  }  }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTickLines: { opacity: true} }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Minor ticks per interval of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>minorTicksPerInterval</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { minorTicksPerInterval: 4 }
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minorTicksPerInterval: 4 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>name of the primaryYAxis</b></td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { name: 'primaryYAxis' }
});
</code>
</td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { name: 'primaryYAxis' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Orientation of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>orientation</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { orientation: 'Vertical' }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Plot offset for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { plotOffset: 0 }
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { plotOffset: 0 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minimum for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.minimum</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { range: { minimum: 10 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>minimum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { minimum: 23 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.maximum</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { range: { maximum: 10 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>maximum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { maximum: 23 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>interval for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.interval</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { range: { interval: 1 }}
});
</code>
</td>
<td>
<b>Property</b>:<i>interval</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { interval: 2 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>RangePadding for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { rangePadding: 'None' }}
});
</code>
</td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { rangePadding: 'None' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Rounding Places in primaryYAxis</b></td>
<td>
<b>Property</b>:<i>roundingPlaces </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { roundingPlaces: 3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { labelFormat: 'n3' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>ScrollBar settings of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>scrollbarSettings </i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { scrollbarSettings : { } }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>TickPosition in primaryYAxis</b></td>
<td>
<b>Property</b>:<i>tickLinesPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { tickLinesPosition: 'Inside' }
});
</code>
</td>
<td>
<b>Property</b>:<i>tickPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { tickPosition: 'Inside' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>valueType of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { valueType: 'DateTime' }
});
</code>
</td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { valueType: 'DateTime' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>visible of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { visible: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { visible: true }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomFactor of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { zoomFactor: 0.3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { zoomFactor: 0.3 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomPosition of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { zoomPosition: 0.3 }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { zoomPosition: 0.3 }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelBorder of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>labelBorder</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { labelBorder: { color: 'red', width: 2} }
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { border: { color: 'red', width: 3 } }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>title of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>title.text</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { title: { text: 'Chart title' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { title: 'Chart title' }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>StripLine of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>stripLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { stripLine: [] }
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { stripLines: [] }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Multilevel labels of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   primaryYAxis: { multiLevelLabels: [] }
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryYAxis: { stripLines: [] }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>skeleton for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeleton</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeleton: 'yMd' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>
<tr>
<td><b>skeleton type for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeletonType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeletonType: 'DateTime' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>
</table>

## Axes

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Alternate grid band</b></td>
<td>
<b>Property</b>:<i>alternateGridBand </i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { alternateGridBand: {  even: { fill: 'red }}}]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Axis line cross value</b></td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { crossesAt: 0 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesAt</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { crossesAt: 4}]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis name with which the axis line has to be crossed</b></td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { crossesInAxis: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>crossesInAxis</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { crossesInAxis: '' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis elements placed with axis line</b></td>
<td>
<b>Property</b>:<i>showNextToAxisLine </i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { showNextToAxisLine : true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>placeNextToAxisLine</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { placeNextToAxisLine: '' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line style</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { axisLine: { color : 'red' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { lineStyle: { color: 'black' } }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>axis line dashArray</b></td>
<td>
<b>Property</b>:<i>axisLine.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { axisLine: { dashArray : '10, 5' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { lineStyle: { dashArray: '10, 5' } }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Offset for axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { axisLine: { offset : 10 } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { plotOffset: 10 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Visible of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.offset</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { axisLine: { visible :  false } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { visible: false }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Width of an axis</b></td>
<td>
<b>Property</b>:<i>axisLine.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { axisLine: { width :  2 } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>lineStyle.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { lineStyle: { width: 3 } }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Column index of an axis</b></td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { columnIndex: 2 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>columnIndex</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { columnIndex: 2 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>span of an axis to place horizontally or vertically</b></td>
<td>
<b>Property</b>:<i>columnSpan</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { columnIndex: 2 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>span</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { span: 2 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label of an axis</b></td>
<td>
<b>Property</b>:<i>crossHairLabel.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { crossHairLabel: { visible: true }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { crossHairTooltip: { enable: true }}]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label color of an axis</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { crossHairTooltip: { fill: 'red' }}]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Crosshair label text style</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>crossHairTooltip.textStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { crossHairTooltip: { textStyle: { } }}]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Desired interval count for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { desiredIntervals: 4}]
});
</code>
</td>
<td>
<b>Property</b>:<i>desiredIntervals</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { desiredIntervals: 4 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Edges primaryYAxis</b></td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { edgeLabelPlacement: 'none' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>edgeLabelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { edgeLabelPlacement: 'Shift'  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Enables trim for axis labels</b></td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { enableTrim: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>enableTrim</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { enableTrim: true  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { enableAutoIntervalOnZooming: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { enableAutoIntervalOnZooming: true  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Specifies the interval of the axis according to the zoomed data of the chart</b></td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { enableAutoIntervalOnZooming: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>enableAutoIntervalOnZooming</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { enableAutoIntervalOnZooming: true  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Font style for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { font: { fontFamily: 'Calibri', fontStyle: 'italic', fontWeight: '', opacity: 0.5, size: 12} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>titleStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { titleStyle: { }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Indexed for category axis</b></td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { isIndexed: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>isIndexed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { isIndexed: true  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Interval type for date time axis</b></td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { intervalType}: 'Auto' } ]
});
</code>
</td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { intervalType: 'Auto  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Inversed axis</b></td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { isInversed: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>isInversed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { isInversed: true  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Custom label format</b></td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelFormat: '{value}K' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelFormat: '{value}K'  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelIntersectAction</b></td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelIntersectAction: 'trim' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelIntersectAction: 'Trim'  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPosition</b></td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelPosition: 'inside' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelPosition: 'Inside'  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelPlacement for category axis</b></td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelPlacement: 'onTicks' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelPlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelPlacement: 'OnTicks'  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Axis label alignment</b></td>
<td>
<b>Property</b>:<i>alignment</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { alignment: 'center' }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Rotation of axis labels</b></td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelRotation: 45 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelRotation: 45  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Log base value for logarithmic axis</b></td>
<td>
<b>Property</b>:<i>logBase</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { logBase: 10 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelRotation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { logBase: 10  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorGridLines: { visible: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorGridLines: { width: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorGridLines: { width: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorGridLines: { color: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorGridLines: { color: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of MajorGridLines</b></td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorGridLines: { dashArray: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorGridLines: { dashArray: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major grid line</b></td>
<td>
<b>Property</b>:<i>majorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorGridLines: { opacity: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorTickLines: { visible: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorTickLines: { width: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorTickLines: { width: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorTickLines: { size: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorTickLines: { height: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of MajorTickLines</b></td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorTickLines: { color: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>majorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { majorTickLines: { color: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of major Tick line</b></td>
<td>
<b>Property</b>:<i>majorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { majorTickLines: { opacity: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>maximum labels of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { maximumLabels: 5 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { maximumLabels: 4 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum labels width of primaryYAxis to trim</b></td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { maximumLabelWidth: 40 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>maximumLabelWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { maximumLabelWidth: 4 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorGridLines: { visible: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorGridLines: { width: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorGridLines: { width: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorGridLines: { color: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorGridLines: { color: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>DashArray of minorGridLines</b></td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorGridLines: { dashArray: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorGridLines.dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorGridLines: { dashArray: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor grid line</b></td>
<td>
<b>Property</b>:<i>minorGridLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorGridLines: { opacity: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTickLines: { visible: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Width of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTickLines: { width: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorTickLines: { width: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Height of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.size</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTickLines: { size: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorTickLines: { height: 2}  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Color of minorTickLines</b></td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTickLines: { color: 'black' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorTickLines: { color: 'black'  }  }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Opacity of minor Tick line</b></td>
<td>
<b>Property</b>:<i>minorTickLines.opacity</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTickLines: { opacity: true} }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Minor ticks per interval of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>minorTicksPerInterval</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { minorTicksPerInterval: 4 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>minorTickLines.color</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minorTicksPerInterval: 4 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>name of the primaryYAxis</b></td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { name: 'primaryYAxis' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { name: 'primaryYAxis' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Orientation of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>orientation</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { orientation: 'Vertical' }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Plot offset for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { plotOffset: 0 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>plotOffset</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { plotOffset: 0 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>minimum for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.minimum</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { range: { minimum: 10 }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>minimum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { minimum: 23 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum for primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.maximum</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { range: { maximum: 10 }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>maximum</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { maximum: 23 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>interval for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>range.interval</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { range: { interval: 1 }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>interval</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { interval: 2 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>RangePadding for  primaryYAxis</b></td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { rangePadding: 'None' }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>rangePadding</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { rangePadding: 'None' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Rounding Places in primaryYAxis</b></td>
<td>
<b>Property</b>:<i>roundingPlaces </i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { roundingPlaces: 3 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { labelFormat: 'n3' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>ScrollBar settings of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>scrollbarSettings </i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { scrollbarSettings : { } }]
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>TickPosition in primaryYAxis</b></td>
<td>
<b>Property</b>:<i>tickLinesPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { tickLinesPosition: 'Inside' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>tickPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { tickPosition: 'Inside' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>valueType of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { valueType: 'DateTime' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { valueType: 'DateTime' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>visible of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { visible: true }]
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { visible: true }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomFactor of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { zoomFactor: 0.3 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomFactor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { zoomFactor: 0.3 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>zoomPosition of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { zoomPosition: 0.3 }]
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomPosition</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { zoomPosition: 0.3 }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>labelBorder of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>labelBorder</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { labelBorder: { color: 'red', width: 2} }]
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { border: { color: 'red', width: 3 } }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>title of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>title.text</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { title: { text: 'Chart title' } }]
});
</code>
</td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { title: 'Chart title' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>StripLine of primaryYAxis</b></td>
<td>
<b>Property</b>:<i>stripLine</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { stripLine: [] }]
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { stripLines: [] }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Multilevel labels of axes</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
$("#container").ejChart({
   axes: [ { multiLevelLabels: [] }]
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { stripLines: [] }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>skeleton for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeleton</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeleton: 'yMd' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>
<tr>
<td><b>skeleton type for an axes</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeletonType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axes: [ { skeletonType: 'DateTime' }]
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<table>

## Rows

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>rows in chart</b></td>
<td>
<b>Property</b>:<i>rowDefinitions</i>
</br>
</br>
<code>
$("#chart").ejChart({
    rowDefinitions: [];
});
</code>
</td>
<td>
<b>Property</b>:<i>rows</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    rows: [];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>unit</b></td>
<td>
<b>Property</b>:<i>unit </i>
</br>
</br>
<code>
$("#container").ejChart({
   rowDefinitions :[{unit : "percentage"}]
});
</code>
</td>
<td>
<b>Not Applicable</b>
</td>
</tr>

<tr>
<td><b>height of rows in chart</b></td>
<td>
<b>Property</b>:<i>rowHeight</i>
</br>
</br>
<code>
$("#chart").ejChart({
    rowDefinitions: [{ rowHeight: '50%'}];
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    rows: [ { height: '300'}];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Line customization</b></td>
<td>
<b>Property</b>:<i>lineColor, lineWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    rowDefinitions: [{ rowHeight: '50%', lineColor: 'brown', lineWidth: 2}];
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    rows: [ { height: '300', border: { width: 2, color: 'brown'}}];
});
chart.appendTo('#chart');
</code></td>
</tr>
</table>

## Series

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>bearFillColor</b></td>
<td>
<b>Property</b>:<i>bearFillColor</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{bearFillColor: 'red' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>bearFillColor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{bearFillColor: 'red' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Border</b></td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ border: { color: 'red', width: 2, dashArray: '10, 5' } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>rows</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ border: { color: 'red', width: 2} }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>BoxPlotMode</b></td>
<td>
<b>Property</b>:<i>boxPlotMode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ boxPlotMode: 'inclusive' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>rows</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ boxPlotMode: 'Inclusive' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Minimum radius of Bubble series</b></td>
<td>
<b>Property</b>:<i>bubbleOptions.minRadius</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ bubbleOptions: { minRadius: 2} }];
});
</code>
</td>
<td>
<b>Property</b>:<i>minRadius</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ minRadius: 2 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Maximum radius of Bubble series</b></td>
<td>
<b>Property</b>:<i>bubbleOptions.maxRadius</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ bubbleOptions: { maxRadius: 10 } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>maxRadius</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ maxRadius: 2 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>bullFillColor</b></td>
<td>
<b>Property</b>:<i>bullFillColor</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{bullFillColor: 'red' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>bullFillColor</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{bullFillColor: 'red' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Cardinal spline tension for spline series</b></td>
<td>
<b>Property</b>:<i>cardinalSplineTension</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ cardinalSplineTension: 0.5 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>cardinalSplineTension</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ cardinalSplineTension: 0.5 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Column Width for rectangle series</b></td>
<td>
<b>Property</b>:<i>columnWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ columnWidth: 0.5 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>columnWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ columnWidth: 0.5 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Column spacing for rectangle series</b></td>
<td>
<b>Property</b>:<i>columnSpacing</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ columnSpacing: 0.5 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>columnSpacing</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ columnSpacing: 0.5 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Topleft radius for rectangle series</b></td>
<td>
<b>Property</b>:<i>cornerRadius.topLeft</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ topLeft: 0 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>cornerRadius.topLeft</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ topLeft: 0 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>topRight radius for rectangle series</b></td>
<td>
<b>Property</b>:<i>cornerRadius.topRight</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ topRight: 0 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>cornerRadius.topRight</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ topRight: 0 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>bottomRight radius for rectangle series</b></td>
<td>
<b>Property</b>:<i>cornerRadius.bottomRight</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ bottomRight: 0 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>cornerRadius.bottomRight</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ bottomRight: 0 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>bottomLeft radius for rectangle series</b></td>
<td>
<b>Property</b>:<i>cornerRadius.bottomLeft</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ bottomLeft: 0 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>cornerRadius.bottomLeft</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ bottomLeft: 0 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>DashArray property</b></td>
<td>
<b>Property</b>:<i>dashArray</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ dashArray: '10, 5' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ dashArray: '10, 5' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>DataSource for series</b></td>
<td>
<b>Property</b>:<i>dataSource</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ dataSource: [] }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dashArray</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ dataSource: [] }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Draw type for Polar series</b></td>
<td>
<b>Property</b>:<i>drawType</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ drawType: 'Line' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>drawType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ drawType: 'Line' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>EmptyPointSettings for series</b></td>
<td>
<b>Property</b>:<i>emptyPointSettings.visible</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ emptyPointSettings: { visible: false } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Empty Point Display mode</b></td>
<td>
<b>Property</b>:<i>emptyPointSettings.displayMode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ displayMode: 'gap' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>emptyPointSettings.displayMode</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ displayMode: 'Average' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Empty Point color</b></td>
<td>
<b>Property</b>:<i>emptyPointSettings.color</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ color: 'red' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>emptyPointSettings.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ fill: 'red' }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Empty Point Border</b></td>
<td>
<b>Property</b>:<i>emptyPointSettings.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ emptyPointSettings:  { color: 'red', width: 2 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ emptyPointSettings:  { color: 'red', width: 2 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Enable animation for series</b></td>
<td>
<b>Property</b>:<i>enableAnimation</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ enableAnimation: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.enable</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ animation: { enable: false }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Animation duration for series</b></td>
<td>
<b>Property</b>:<i>animationDuration</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ animationDuration: 1000 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.duration</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ animation: { duration: 1000 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Animation delay for series</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>animation.duration</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ animation: { delay: 100 }];
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Drag settings for series</b></td>
<td>
<b>Property</b>:<i>dragSettings</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ dragSettings: { mode: 'X' } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Errorbar settings for series</b></td>
<td>
<b>Property</b>:<i>errorBarSettings</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ errorBarSettings: {  } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>errorBarSettings</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ {errorBarSettings: { }}];
});
</code>
</td>
</tr>

<tr>
<td><b>Closed series</b></td>
<td>
<b>Property</b>:<i>isClosed</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ isClosed: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>isClosed</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { isClosed: true }];
});
</code>
</td>
</tr>

<tr>
<td><b>Stacking Property for series</b></td>
<td>
<b>Property</b>:<i>isStacking</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ isStacking: true }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Line cap for series</b></td>
<td>
<b>Property</b>:<i>lineCap</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ lineCap: 'butt' }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Line join for series</b></td>
<td>
<b>Property</b>:<i>lineCap</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ lineJoin: 'round' }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Opacity for series</b></td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ opacity: 0.7 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>errorBarSettings</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { opacity: 0.7 }];
});
</code>
</td>
</tr>

<tr>
<td><b>Outlier settings of series</b></td>
<td>
<b>Property</b>:<i>outLierSettings</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ outLierSettings: { shape: 'rectangle' , size: { height: 30, width: 20}} }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Palette</b></td>
<td>
<b>Property</b>:<i>palette</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ palette: "ColorFieldName" }];
});
</code>
</td>
<td>
<b>Property</b>:<i>pointColorMapping</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { pointColorMapping: 'color' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Positive fill for waterfall series</b></td>
<td>
<b>Property</b>:<i>positiveFill</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ positiveFill: "red" }];
});
</code>
</td>
<td>
<b>Property</b>:<i>pointColorMapping</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { pointColorMapping: 'color' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Show average value in box and whisker series</b></td>
<td>
<b>Property</b>:<i>showMedian</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ showMedian: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>pointColorMapping</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { showMean: false }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>To group the series of stacking collection.</b></td>
<td>
<b>Property</b>:<i>stackingGroup</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ stackingGroup: 'group' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>stackingGroup</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { stackingGroup: 'group' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Specifies the type of the series to render in chart.</b></td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ type: 'Line' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { type: 'Line' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Defines the visibility of the series.</b></td>
<td>
<b>Property</b>:<i>visibility</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ visibility: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { visible: true }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Enables or disables the visibility of legend item.</b></td>
<td>
<b>Property</b>:<i>visibleOnLegend </i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ visibleOnLegend : true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>toggleVisibility</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: [ { toggleVisibility: true }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Specifies the different types of spline curve.</b></td>
<td>
<b>Property</b>:<i>splineType </i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ splineType : 'Natural' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>splineType</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendSettings: [ { splineType: 'Natural' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Specifies the name of the x-axis that has to be associated with this series. Add an axis instance with this name to axes collection.</b></td>
<td>
<b>Property</b>:<i>xAxisName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ xAxisName : 'secondaryXAxis' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>xAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { xAxisName: 'secondaryXAxis' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains x value for the series.</b></td>
<td>
<b>Property</b>:<i>xName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ xName : 'x' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>xName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { xName: 'x' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Specifies the name of the y-axis that has to be associated with this series. Add an axis instance with this name to axes collection.</b></td>
<td>
<b>Property</b>:<i>yAxisName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ yAxisName : 'secondaryYAxis' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>yAxisName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { yAxisName: 'secondaryYAxis' }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains y value for the series.</b></td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ yName : 'y' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { yName: 'y' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains high value for the series.</b></td>
<td>
<b>Property</b>:<i>high</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ high : 'y' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>high</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { high: 'y' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains low value for the series.</b></td>
<td>
<b>Property</b>:<i>low</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ low : 'y' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>low</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { low: 'y' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains close value for the series.</b></td>
<td>
<b>Property</b>:<i>close</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ close : 'y' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>close</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { close: 'y' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains open value for the series.</b></td>
<td>
<b>Property</b>:<i>open</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ open : 'y' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>open</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { open: 'y' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Option to add trendlines to chart.</b></td>
<td>
<b>Property</b>:<i>trendLines</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines : [{}] }];
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ trendLines : [{}] }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Options for customizing the appearance of the series or data point while highlighting.</b></td>
<td>
<b>Property</b>:<i>highlightSettings</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ highlightSettings : {} }];
});
</code>
</td>
<td>
Not applicable.
</td>
</tr>

<tr>
<td><b>Options for customizing the appearance of the series/data point on selection.</b></td>
<td>
<b>Property</b>:<i>selectionSettings </i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ selectionSettings  : {} }];
});
</code>
</td>
<td>
Not applicable.
</td>
</tr>

</table>

## marker

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>visibility of marker</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { visible: true  } ];
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { marker: { visible: false } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Fill for marker</b></td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { fill : 'red' } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { fill : 'red' } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Opacity for marker</b></td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { opacity : 0.5 } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { opacity : 0.5 } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Shape of marker</b></td>
<td>
<b>Property</b>:<i>shape</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { shape : 'Circle' } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>shape</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { shape : 'Triangle' } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>ImageUrl of marker</b></td>
<td>
<b>Property</b>:<i>imageUrl</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { imageUrl : '' } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>imageUrl</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { imageUrl : '' } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Border of marker</b></td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { border : { width: 2, color: 'red' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>shape</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { border : { width: 2, color: 'red' } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Height of marker</b></td>
<td>
<b>Property</b>:<i>size.height</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { size: { height: 30} } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { height: 25 } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Width of marker</b></td>
<td>
<b>Property</b>:<i>size.width</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { size: { width: 30} } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { width: 25 } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Width of marker</b></td>
<td>
<b>Property</b>:<i>size.width</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: { size: { width: 30} } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { width: 25 } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>DataLabelSettings of marker</b></td>
<td>
<b>Property</b>:<i>marker.dataLabel</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>marker.dataLabel</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Visibility of dataLabel</b></td>
<td>
<b>Property</b>:<i>dataLabel.visible</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { visible: true } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.visible</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { visible: true } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Text mapping name of dataLabel</b></td>
<td>
<b>Property</b>:<i>dataLabel.textMappingName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { textMappingName: '' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.name</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { name: '' } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Fill color of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.fill</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { fill: 'pink' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { fill: 'pink' } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Opacity of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.opacity</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { opacity: 0.6 } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { opacity: 0.4 } } }];
});
chart.appendTo('#chart);
</code>

</td>
</tr>

<tr>
<td><b>Text position of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.textPosition</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { textPosition: 'middle' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.position</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { position: 'Top' } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Alignment of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.verticalAlignment</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { verticalAlignment: 'near' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.alignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { alignment: 'Near' } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Border of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { border: { color: 'blue', width: 2, opacity: 0.4} } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.alignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { border: { color: 'blue', width: 2 } } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Offset for data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.offset</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { offset: { x: 5, y: 6 }} } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Margin of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { margin: { top: 10, bottom: 10, left: 10, right: 10}} } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.margin</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: { dataLabel: { margin: { top: 10, bottom: 10, left: 10, right: 10 } } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Font of data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { font: { fontFamily: 'SegoeUI', fontStyle: 'italic', fontWeight: '600', opacity: 0.5, size: 12, color: 'red' }} } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.margin</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: {dataLabel: { font: { fontFamily: 'SegoeUI', fontStyle: 'italic', fontWeight: '600', opacity: 0.5, size: 12, color: 'red' }} } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>HTML template in dataLabel</b></td>
<td>
<b>Property</b>:<i>dataLabel.template</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { template: '<div>Chart</div>' } } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataLabel.template</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: {dataLabel: { template: '<div>Chart</div>' } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Rounded corner radius X</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>dataLabel.rx</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: {dataLabel: { rx: 10 } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Rounded corner radius Y</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>dataLabel.ry</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [{ marker: {dataLabel: { ry: 10 } } }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Maximum Label width for data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.maximumLabelWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { maximumLabelWidth: 20}} } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Enable wrapping of text for data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.enableWrap</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { enableWrap: true }} } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>To show contrast color for data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.showContrastColor</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { showContrastColor: true }} } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>To show edge label for data label</b></td>
<td>
<b>Property</b>:<i>dataLabel.showEdgeLabels</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ marker: {dataLabel: { showEdgeLabels: true }} } }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

</table>

## TrendLines

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Trendlines settings</b></td>
<td>
<b>Property</b>:<i>series.trendLines</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: []}]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.trendLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: []}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Visibility of trendline</b></td>
<td>
<b>Property</b>:<i>trendLines.visibility</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ visibility: true ]}]
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Type of trendLine</b></td>
<td>
<b>Property</b>:<i>trendLines.type</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [type: 'linear' ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.type</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ type: 'Polynomial']}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Name of trendLine</b></td>
<td>
<b>Property</b>:<i>trendLines.name</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ name: 'trendLine' ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.name</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ name: 'trendLine']}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Period of trendLine</b></td>
<td>
<b>Property</b>:<i>trendLines.period</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ period: 45 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.period</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ period: 45]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Polynomial order for Polynomial type trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.polynomialOrder</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ polynomialOrder: 3 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.polynomialOrder</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ polynomialOrder: 3]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Backward forecost for  trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.backwardforecast</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ backwardforecast: 3 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.backwardforecast</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ backwardforecast: 3]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Forward forecost for  trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.forwardForecast</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ forwardForecast: 3 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.forwardForecast</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ forwardForecast: 3]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Fill for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.fill</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ fill: '#EEFFCC' ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.fill</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ fill: 'EEFFCC']}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Width for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.width</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ width: 2 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.width</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ width: 2]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Intercept value for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.intercept</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ intercept: 2 ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.intercept</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ intercept: 2]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Legend shape for trendLines</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>trendLines.legendShape</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ legendShape: 'Rectangle']}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Animation settings for trendLines</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>trendLines.animation</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ animation: { enable: true }]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Marker settings for trendLines</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>trendLines.marker</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ {marker: { visible: true }}]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Tooltip for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.tooltip</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ { tooltip: { } } ]}]
});
</code>
</td>
<td>
<b>Property</b>:<i>trendLines.enableTooltip</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    series: [ { trendLines: [ {enableTooltip:  true }]}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>DashArray for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.dashArray</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ { dashArray: '10, 5' } ]}]
});
</code>
</td>
<td>
Not Applicable.
</td>
</tr>

<tr>
<td><b>Visible on legend for trendLines</b></td>
<td>
<b>Property</b>:<i>trendLines.visibleOnLegend</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ trendLines: [ { visibleOnLegend: true } ]}]
});
</code>
</td>
<td>
Not Applicable.
</td>
</tr>
</table>

## StripLines

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Default behaviour for striplines</b></td>
<td>
<b>Property</b>:<i>primaryXAxis.stripLines</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { visible: true }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>primaryXAxis.stripLines</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { visible: true }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>border for stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.borderColor</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { borderColor: 'pink' }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { border: { color: 'red', width: 2} }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Background color for stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.color</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { color: 'pink' }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { color: 'red'}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Start value for stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.start</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { start: 10 }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.start</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { start: 5}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>End value for stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.end</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { end: 10 }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.end</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { end: 5}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>StartfromAxis for stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.startFromAxis</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { startFromAxis: true }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.startFromAxis</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { startFromAxis: true}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Text in stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.text</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { text: 'StripLine; }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.text</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { text: 'stripline'}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Text alignment in stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.textAlignment</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { textAlignment: 'Far; }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.horizontalAlignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { horizontalAlignment: 'Far'}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Vertical Text alignment in stripline</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>stripLines.verticalAlignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { verticalAlignment: 'Far'}]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Size of stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.width</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { width: 10; }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.size</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { size: 10 }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>ZIndex of stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.zIndex</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { zIndex: 'Behind' }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.size</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { zIndex: 'Behind' }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Font style  of stripline</b></td>
<td>
<b>Property</b>:<i>stripLines.fontStyle</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { stripLines: [ { fontStyle: {} }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>stripLines.textStyle</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { stripLines: [ { textStyle: {} }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

</table>

## Multilevel Labels

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Default behaviour for multilevelLabels</b></td>
<td>
<b>Property</b>:<i>primaryXAxis.multilevelLabels</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { visible: true }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>primaryXAxis.multilevelLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { multilevelLabels: [ { }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Default behaviour for multilevelLabels</b></td>
<td>
<b>Property</b>:<i>primaryXAxis.multilevelLabels</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { visible: true }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>primaryXAxis.multilevelLabels</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { multilevelLabels: [ { }]}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Text alignment for multilevelLabels</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.textAlignment</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { textAlignment: 'Near' }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multilevelLabels.alignment</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { multilevelLabels: [ {alignment: 'Near' }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Text overflow for multilevelLabels</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.textOverFlow</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { textOverFlow: 'Trim' }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.overFlow</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    primaryXAxis: { multilevelLabels: [ {overFlow: 'Trim' }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Border for multilevelLabels</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { border: { width: 2, color: 'red', type: 'brace' } }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     primaryXAxis: { multilevelLabels: [ { border: { width: 2, color: 'red', type: 'brace' } }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Start value for label</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.start</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { start: 45 } }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.categories.start</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     primaryXAxis: { multilevelLabels: [ { categories: [ { start: 45}] } }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>End value for label</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.start</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { end: 45 } }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.categories.end</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     primaryXAxis: { multilevelLabels: [ { categories: [ { end: 45}] } }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Text for label</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.text</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { text: 'Start' } }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.categories.text</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     primaryXAxis: { multilevelLabels: [ { categories: [ { text: 'text' }] } }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>maximum text width for label</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.maximumTextWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { maximumTextWidth: 10 } }]}
});
</code>
</td>
<td>
<b>Property</b>:<i>multiLevelLabels.categories.maximumTextWidth</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
     primaryXAxis: { multilevelLabels: [ { categories: [ { maximumTextWidth: 20 }] } }]}
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>level of labels</b></td>
<td>
<b>Property</b>:<i>multiLevelLabels.level</i>
</br>
</br>
<code>
$("#chart").ejChart({
    primaryXAxis: { multilevelLabels: [ { level: 2 } }]}
});
</code>
</td>
<td>
Not applicable. Categories are used
</td>
</tr>

</table>

## Methods

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>animation for series</b></td>
<td>
<b>Property</b>:<i>chart.animate</i>
</br>
</br>
<code>
$("#chart").ejChart({
    animate: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Redraw for chart</b></td>
<td>
<b>Property</b>:<i>chart.redraw</i>
</br>
</br>
<code>
$("#chart").ejChart({
    redraw: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chart.refresh()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({

});
chart.appendTo('#chart');
chart.width = '400';
chart.refresh();
</code>
</td>
</tr>

<tr>
<td><b>Export</b></td>
<td>
<b>Property</b>:<i>chart.export()</i>
</br>
</br>
<code>
$("#chart").ejChart({
    export: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chart.export()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({

});
chart.export('JPEG', 'chart');
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Print</b></td>
<td>
<b>Property</b>:<i>chart.print()</i>
</br>
</br>
<code>
$("#chart").ejChart({
    print: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chart.print()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({

});
chart.print('chart');
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>AddSeries</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>chart.addSeries()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({

});
chart.appendTo('#chart');
chart.addSeries();
</code>
</td>
</tr>

<tr>
<td><b>RemoveSeries</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>chart.removeSeries()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({

});
chart.appendTo('#chart');
chart.removeSeries();
</code>
</td>
</tr>
</table>

## Events

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Fires on annotation click</b></td>
<td>
<b>Property</b>:<i>annotationClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotationClick: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires after animation</b></td>
<td>
<b>Property</b>:<i>animationComplete</i>
</br>
</br>
<code>
$("#chart").ejChart({
    animationComplete: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>animationComplete()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    animationComplete: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on axis label click</b></td>
<td>
<b>Property</b>:<i>axisLabelClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axisLabelClick: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before axis label render</b></td>
<td>
<b>Property</b>:<i>axisLabelRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axisLabelRendering: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>axisLabelRender()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axisLabelRender: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on axis label mouseMove</b></td>
<td>
<b>Property</b>:<i>axisLabelMouseMove</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axisLabelMouseMove: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires on axis label initialize</b></td>
<td>
<b>Property</b>:<i>axisLabelInitialize</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axisLabelInitialize: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before axis range calculation</b></td>
<td>
<b>Property</b>:<i>axesRangeCalculate</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axesRangeCalculate: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>axisRangeCalculated()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axisRangeCalculated: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on axis title rendering</b></td>
<td>
<b>Property</b>:<i>axisTitleRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    axisTitleRendering: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires on after chart resize</b></td>
<td>
<b>Property</b>:<i>afterResize</i>
</br>
</br>
<code>
$("#chart").ejChart({
    afterResize: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires on before chart resize</b></td>
<td>
<b>Property</b>:<i>beforeResize</i>
</br>
</br>
<code>
$("#chart").ejChart({
    beforeResize: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>resized</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    resized: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on chart click</b></td>
<td>
<b>Property</b>:<i>chartClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    chartClick: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chartMouseClick</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartMouseClick: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on chart mouse move</b></td>
<td>
<b>Property</b>:<i>chartMouseMove</i>
</br>
</br>
<code>
$("#chart").ejChart({
    chartMouseMove: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chartMouseMove</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartMouseMove: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on chart mouse leave</b></td>
<td>
<b>Property</b>:<i>chartMouseLeave</i>
</br>
</br>
<code>
$("#chart").ejChart({
    chartMouseLeave: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>chartMouseLeave</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartMouseLeave: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on before chart double click</b></td>
<td>
<b>Property</b>:<i>chartDoubleClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    chartDoubleClick: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires on chart mouse up</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>chartmouseUp</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartmouseUp: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on chart mouse down</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>chartmouseDown</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartmouseDown: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires during the calculation of chart area bounds. You can use this event to customize the bounds of chart area</b></td>
<td>
<b>Property</b>:<i>chartAreaBoundsCalculate</i>
</br>
</br>
<code>
$("#chart").ejChart({
    chartAreaBoundsCalculate: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires when the dragging is started</b></td>
<td>
<b>Property</b>:<i>dragStart</i>
</br>
</br>
<code>
$("#chart").ejChart({
    dragStart: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires while dragging</b></td>
<td>
<b>Property</b>:<i>dragging</i>
</br>
</br>
<code>
$("#chart").ejChart({
    dragging: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires when the dragging is completed</b></td>
<td>
<b>Property</b>:<i>dragEnd</i>
</br>
</br>
<code>
$("#chart").ejChart({
    dragEnd: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>dragComplete</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    dragComplete: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires when chart is destroyed completely.</b></td>
<td>
<b>Property</b>:<i>destroy</i>
</br>
</br>
<code>
$("#chart").ejChart({
    destroy: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires after chart is created.</b></td>
<td>
<b>Property</b>:<i>create</i>
</br>
</br>
<code>
$("#chart").ejChart({
    create: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>loaded</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    loaded: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires before rendering the data labels.</b></td>
<td>
<b>Property</b>:<i>displayTextRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    displayTextRendering: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>textRender</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    textRender: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires, when error bar is rendering.</b></td>
<td>
<b>Property</b>:<i>errorBarRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    errorBarRendering: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires during the calculation of legend bounds.</b></td>
<td>
<b>Property</b>:<i>legendBoundsCalculate</i>
</br>
</br>
<code>
$("#chart").ejChart({
    legendBoundsCalculate: () {

    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires on clicking the legend item.</b></td>
<td>
<b>Property</b>:<i>legendItemClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    legendItemClick: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires when moving mouse over legend item</b></td>
<td>
<b>Property</b>:<i>legendItemMouseMove</i>
</br>
</br>
<code>
$("#chart").ejChart({
    legendItemMouseMove: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering the legend item.</b></td>
<td>
<b>Property</b>:<i>legendItemRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    legendItemRendering: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>legendRender</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    legendRender: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires before loading the chart.</b></td>
<td>
<b>Property</b>:<i>load</i>
</br>
</br>
<code>
$("#chart").ejChart({
    load: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>load</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    load: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires, when multi level labels are rendering.</b></td>
<td>
<b>Property</b>:<i>multiLevelLabelRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    multiLevelLabelRendering: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>axisMultiLabelRender </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    axisMultiLabelRender : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires on clicking a point in chart.</b></td>
<td>
<b>Property</b>:<i>pointRegionClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    pointRegionClick: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>pointClick </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    pointClick : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires when mouse is moved over a point.</b></td>
<td>
<b>Property</b>:<i>pointRegionMouseMove</i>
</br>
</br>
<code>
$("#chart").ejChart({
    pointRegionMouseMove: () {
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>pointMove </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    pointMove : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires before rendering chart.</b></td>
<td>
<b>Property</b>:<i>preRender</i>
</br>
</br>
<code>
$("#chart").ejChart({
    preRender: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires when point render.</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>pointRender </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    pointRender : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires after selected the data in chart.</b></td>
<td>
<b>Property</b>:<i>rangeSelected</i>
</br>
</br>
<code>
$("#chart").ejChart({
    rangeSelected: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires after selecting a series.</b></td>
<td>
<b>Property</b>:<i>seriesRegionClick</i>
</br>
</br>
<code>
$("#chart").ejChart({
    seriesRegionClick: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering a series.</b></td>
<td>
<b>Property</b>:<i>seriesRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    seriesRendering: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>seriesRender </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    seriesRender : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires before rendering the marker symbols.</b></td>
<td>
<b>Property</b>:<i>symbolRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    symbolRendering: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering the trendline</b></td>
<td>
<b>Property</b>:<i>trendlineRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    trendlineRendering: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering the Chart title.</b></td>
<td>
<b>Property</b>:<i>titleRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    titleRendering: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering the Chart sub title.</b></td>
<td>
<b>Property</b>:<i>subTitleRendering</i>
</br>
</br>
<code>
$("#chart").ejChart({
    subTitleRendering: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering the tooltip. </b></td>
<td>
<b>Property</b>:<i>toolTipInitialize</i>
</br>
</br>
<code>
$("#chart").ejChart({
    toolTipInitialize: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>tooltipRender </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    tooltipRender : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires before rendering crosshair tooltip in axis</b></td>
<td>
<b>Property</b>:<i>trackAxisToolTip</i>
</br>
</br>
<code>
$("#chart").ejChart({
    trackAxisToolTip: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Fires before rendering trackball tooltip.</b></td>
<td>
<b>Property</b>:<i>trackToolTip</i>
</br>
</br>
<code>
$("#chart").ejChart({
    trackToolTip: () {
    }
});
</code>
</td>
<td>
Not applicable
</td>
</tr>

<tr>
<td><b>Event triggered when scroll starts.</b></td>
<td>
<b>Property</b>:<i>scrollStart</i>
</br>
</br>
<code>
$("#chart").ejChart({
    scrollStart: () {
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>scrollStart </i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    scrollStart : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Event triggered when scroll ends.</b></td>
<td>
<b>Property</b>:<i>scrollEnd</i>
</br>
</br>
<code>
$("#chart").ejChart({
    scrollEnd: () {
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>scrollEnd</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    scrollEnd: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Event triggered when scroll changes.</b></td>
<td>
<b>Property</b>:<i>scrollChange</i>
</br>
</br>
<code>
$("#chart").ejChart({
    scrollChange: () {
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>scrollChange</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    scrollChange: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

<tr>
<td><b>Fires while performing rectangle zooming in chart.</b></td>
<td>
<b>Property</b>:<i>zoomComplete</i>
</br>
</br>
<code>
$("#chart").ejChart({
    zoomComplete: () {
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomComplete</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    zoomComplete: () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

## Chart properties

</table>

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>selected data index</b></td>
<td>
<b>Property</b>:<i>selectedDataPointIndexes:</i>
</br>
</br>
<code>
$("#chart").ejChart({
    selectedDataPointIndexes: [ { seriesIndex: 0, pointIndex: 1}]
});
</code>
</td>
<td>
<b>Property</b>:<i>selectedDataIndexes</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
selectedDataIndexes: [ { series: 0, point: 1}]
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>sideBySideSeriesPlacement for column based series</b></td>
<td>
<b>Property</b>:<i>sideBySideSeriesPlacement:</i>
</br>
</br>
<code>
$("#chart").ejChart({
    sideBySideSeriesPlacement
});
</code>
</td>
<td>
<b>Property</b>:<i>sideBySidePlacement</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
 sideBySidePlacement: true
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>ZoomSettings</b></td>
<td>
<b>Property</b>:<i>zooming:</i>
</br>
</br>
<code>
$("#chart").ejChart({
    zooming: {
        enable: true,
        enabledeferredZoom: true,
        enablePinch: true,
        enableMouseWheel: true,
        enableSrollBar: true,
        toolBarItems: [],
        type: 'X'

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>zoomSettings</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
 zoomSettings: {
     enable: true,
     enablePinchZooming: true,
     enableDefferedZooming: true
     enableMouseWheelZooming: true,
     enableSelectionZooming: true,
     enableScrollBar: true
 }
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Background color of the chart</b></td>
<td>
<b>Property</b>:<i>background </i>
</br>
</br>
<code>
$("#container").ejChart({
   background: 'transparent'
});
</code>
</td>
<td>
<b>Property</b>:<i>background</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    background: '#EEFFCC'
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>URL of the image to be used as chart background.</b></td>
<td>
<b>Property</b>:<i>backGroundImageUrl </i>
</br>
</br>
<code>
$("#container").ejChart({
   backGroundImageUrl : '../images/chart/wheat.png'
});
</code>
</td>
<td>
<b>Not Applicable</b>
</td>
</tr>

<tr>
<td><b>Customizing border of the chart</b></td>
<td>
<b>Property</b>:<i>border </i>
</br>
</br>
<code>
$("#container").ejChart({
   border: { width: 2, color: '#CCEEFF', opacity: 0.5}
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    border: { width: 2, color: '#CCEEFF'}
});
chart.appendTo('#chart');
</code></td>
</tr>

<tr>
<td>This provides options for customizing export settings</td>
<td>
<b>Property</b>:<i>exportSettings</i>
</br>
</br>
<code>
$("#container").ejChart({
   exportSettings: { filename : "chart", angle: '45' }
});
</code>
</td>
<td>
<b>Property</b>:<i>export()</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    border: { width: 2, color: '#CCEEFF'}
});
chart.appendTo('#chart');
chart.export(<ExportType>type, fileName);
</code></td>
</tr>

<tr>
<td>ChartArea customization</td>
<td>
<b>Property</b>:<i>chartArea</i>
</br>
</br>
<code>
$("#container").ejChart({
   chartArea: { background: 'transparent', border: { opacity: 0.3, color: 'red', width: 2}}
});
</code>
</td>
<td>
<b>Property</b>:<i>chartArea</i>
</br>
</br>
<code>
let chart: Chart = new Chart({
    chartArea: { background: 'transparent', border: { width: 2, color: '#CCEEFF'} }
});
chart.appendTo('#chart');
chart.export(<ExportType>type, fileName);
</code>
</td>
</tr>

</table>