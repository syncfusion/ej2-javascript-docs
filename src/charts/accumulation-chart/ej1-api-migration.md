---
title: "Accumulation Chart API Migration | TypeScript "

component: "Accumulation Chart"

description: "This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2."
---

# Migration from Essential JS 1

This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2.

## Accumulation Chart

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>annotations</b></td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
annotations: [{ }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>background</b></td>
<td>
<b>Property</b>:<i>background</i>
</br>
</br>
<code>
$("#chart").ejChart({
    background: '#DDCCEE'
});
</code>
</td>
<td>
<b>Property</b>:<i>background</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    background: 'DDCCEE'
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>border</b></td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    border: { color: 'red' , width: 2, opacity: 0.5}
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    border: { color: 'red', width: 2}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>dataSource</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   dataSource: [ ];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Animation after legend click</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>enableAnimation</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   enableAnimation: true
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Persisting component's state between page reloads.</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>enablePersistance</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   enablePersistance: true
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Enabling smart labels</b></td>
<td>
<b>Property</b>:<i>series.enableSmartLabels</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [ { enableSmartLabels: true}]
});
</code>
</td>
<td>
<b>Property</b>:<i>enableSmartLabels</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   enableSmartLabels: true
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Height of Chart</b></td>
<td>
<b>Property</b>:<i>size.height</i>
</br>
</br>
<code>
$("#chart").ejChart({
    size: { height: '400' }
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   height: '400'
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Multi selection</b></td>
<td>
<b>Property</b>:<i>selectionSettings.type</i>
</br>
</br>
<code>
$("#chart").ejChart({
    selectionSettings: {
        type: 'multiple'
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>isMultiSelect</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   isMultiSelect: true
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>legend Settings</b></td>
<td>
<b>Property</b>:<i>legend</i>
</br>
</br>
<code>
$("#chart").ejChart({
    legend: { }
});
</code>
</td>
<td>
<b>Property</b>:<i>legendSettings</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   legendSettings: { }
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Margin for the chart</b></td>
<td>
<b>Property</b>:<i>margin</i>
</br>
</br>
<code>
$("#chart").ejChart({
    margin: { top: 20, bottom: 23, right: 15, left: 10 }
});
</code>
</td>
<td>
<b>Property</b>:<i>margin</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   margin: { top: 20, bottom: 23, right: 15, left: 10 }
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>SelectedDataIndexes</b></td>
<td>
<b>Property</b>:<i>selectedDataPointIndexes </i>
</br>
</br>
<code>
$("#chart").ejChart({
    selectedDataPointIndexes : [{}]
});
</code>
</td>
<td>
<b>Property</b>:<i>selectedDataIndexes </i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   selectedDataIndexes : [ { series: 0, point: 1}]
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Selection Mode</b></td>
<td>
<b>Property</b>:<i>selectionSettings.mode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    selectionSettings: { mode: 'Point'}
});
</code>
</td>
<td>
<b>Property</b>:<i>selectionMode </i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   selectionMode : 'Point'
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Series</b></td>
<td>
<b>Property</b>:<i>series</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: []
});
</code>
</td>
<td>
<b>Property</b>:<i>series</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  series: []
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Title text</b></td>
<td>
<b>Property</b>:<i>title.text</i>
</br>
</br>
<code>
$("#chart").ejChart({
   title: { text: 'Pie Chart' }
});
</code>
</td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  title: 'Pie Chart'
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Title Styles</b></td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
$("#chart").ejChart({
   title: { text: 'Pie Chart' }
});
</code>
</td>
<td>
<b>Property</b>:<i>titleStyle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  titleStyle: { fontFamily: 'SegoeUI'}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Sub Title text</b></td>
<td>
<b>Property</b>:<i>subTitle.text</i>
</br>
</br>
<code>
$("#chart").ejChart({
   subTitle: { text: 'Pie Chart' }
});
</code>
</td>
<td>
<b>Property</b>:<i>subTitle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  subTitle: 'Pie Chart'
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Sub title Styles</b></td>
<td>
<b>Property</b>:<i>title</i>
</br>
</br>
<code>
$("#chart").ejChart({
   title: { text: 'Pie Chart' }
});
</code>
</td>
<td>
<b>Property</b>:<i>subTitleStyle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  subTitleStyle: { fontFamily: 'SegoeUI'}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>tooltip</b></td>
<td>
<b>Property</b>:<i>series.toolTip</i>
</br>
</br>
<code>
$("#chart").ejChart({
   series: [ { tooltip: { }}]
});
</code>
</td>
<td>
<b>Property</b>:<i>tooltip</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
  tooltip: { }
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Width of Chart</b></td>
<td>
<b>Property</b>:<i>size.width</i>
</br>
</br>
<code>
$("#chart").ejChart({
    size: { width: '400' }
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
   width: '400'
});
pie.appendTo('#chart');
</code></td>
</tr>
</table>

## Annotation

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>annotations</b></td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
annotations: [{ }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>content</b></td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{content: '<div>Pie Chart</div>}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
annotations: [{content: '<div>Pie Chart</div>'}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>coordinateUnits</b></td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
$("#chart").ejChart({
    annotations: [{coordinateUnit: 'Pixel'}];
});
</code>
</td>
<td>
<b>Property</b>:<i>annotations</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    annotations: [{coordinateUnit: 'Pixel'}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>description</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>description</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    annotations: [{description: 'Pixel'}];
});
pie.appendTo('#chart');
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
annotations: [{ x: '100'}]
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
let chart: AccumulationChart = new AccumulationChart({
annotations: [{ y: '100'}]
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
<td><b>series</b></td>
<td>
<b>Property</b>:<i>series</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{}];
});
</code>
</td>
<td>
<b>Property</b>:<i>series</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>animation for series</b></td>
<td>
<b>Property</b>:<i>enableAnimation</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ enableAnimation: true}];
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.enable</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ animation: { enable: true }}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>animation duration for series</b></td>
<td>
<b>Property</b>:<i>animationDuration</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ annimationDuration: 1000}];
});
</code>
</td>
<td>
<b>Property</b>:<i>animation.duration</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ animation: { duration: 1000 }}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>animation delay for series</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>animation.duration</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ animation: { delay: 100 }}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Border for series</b></td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ border: { color: 'pink', width: 2, dashArray: '10,4' }}];
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ border: { color: 'red', width: 2 }}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>DataLabel for series</b></td>
<td>
<b>Property</b>:<i>dataLabel</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ dataLabel: {}}];
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ dataLabel: { }}];
});
pie.appendTo('#chart');
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
    series: [{ dataSource: [{}] }];
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ dataSource: [{ }]}];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>enableTooltip for series</b></td>
<td>
<b>Property</b>:<i>tooltip.visible</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ tooltip: { visible: true } }];
});
</code>
</td>
<td>
<b>Property</b>:<i>enableTooltip</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ enableTooltip: true }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>start angle</b></td>
<td>
<b>Property</b>:<i>startAngle</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ startAngle: 80 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>startAngle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ startAngle: 90 }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>end angle</b></td>
<td>
<b>Property</b>:<i>endAngle</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ endAngle: 80 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>endAngle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ endAngle: 90 }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>explode</b></td>
<td>
<b>Property</b>:<i>explode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ explode: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>explode</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ explode: true }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>explodeAll</b></td>
<td>
<b>Property</b>:<i>explodeAll</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ explodeAll: true }];
});
</code>
</td>
<td>
<b>Property</b>:<i>explodeAll</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ explodeAll: true }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>explodeIndex</b></td>
<td>
<b>Property</b>:<i>explode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ explodeIndex: 0 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>explodeIndex</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ explodeIndex: 1 }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>explodeOffset</b></td>
<td>
<b>Property</b>:<i>explodeOffset</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ explodeOffset: '30%' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>explodeOffset</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ explodeOffset: '30%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>gapRatio</b></td>
<td>
<b>Property</b>:<i>gapRatio</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ gapRatio: 0.6 }];
});
</code>
</td>
<td>
<b>Property</b>:<i>gapRatio</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ gapRatio: 0.6 }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>gapWidth</b></td>
<td>
<b>Property</b>:<i>gapWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ gapWidth: 0.6 }];
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>inner radius of the accumulation chart</b></td>
<td>
<b>Property</b>:<i>innerRadius </i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ innerRadius : '30%'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>innerRadius </i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ innerRadius : '30%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Legend shape of the series</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>legendShape</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ legendShape : 'Rectangle' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>name of the series</b></td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ name : '30%'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>name</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ name : '30%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>neck height for funnel series</b></td>
<td>
<b>Property</b>:<i>neckHeight</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ neckHeight : '30%'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>neckHeight</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ neckHeight : '30%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>neck width for funnel series</b></td>
<td>
<b>Property</b>:<i>neckWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ neckWidth : '30%'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>neckWidth</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ neckWidth : '30%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>opacity for series</b></td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ opacity : 0.4  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ opacity : 0.5 }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>palettes for series</b></td>
<td>
<b>Property</b>:<i>palette</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ palette : []  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>palettes</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ palettes : [] }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>point color mapping name for series</b></td>
<td>
<b>Property</b>:<i>pointColorMappingName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ pointColorMappingName : 'color'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>pointColorMapping</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ pointColorMappingName : 'color' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Mode of pyramid series</b></td>
<td>
<b>Property</b>:<i>pyramidMode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ pyramidMode : 'Surface'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>pyramidMode</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ pyramidMode : 'Linear' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>query for datasource for series</b></td>
<td>
<b>Property</b>:<i>pyramidMode</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ query : ''  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>query</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ query : '' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Radius of Pie series</b></td>
<td>
<b>Property</b>:<i>pieCoefficient</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ pieCoefficient : 0.5  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>radius</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ radius: '50%' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Selection Style of Accumulation chart</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>selectionStyle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ selectionStyle: '' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>tooltip Mapping name</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>tooltipMappingName</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ tooltipMappingName: '' }];
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Type of series </b></td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ type : 'Pie'  }];
});
</code>
</td>
<td>
<b>Property</b>:<i>type</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: [{ type: 'Pie' }];
});
pie.appendTo('#chart');
</code></td>
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
let chart: AccumulationChart = new AccumulationChart({
    series: [ { xName: 'x' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains x value for the series.</b></td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ yName : 'x' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    series: [ { yName: 'x' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Name of the property in the datasource that contains x value for the series.</b></td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ yName : 'x' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>yName</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    series: [ { yName: 'x' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Width of funnel series</b></td>
<td>
<b>Property</b>:<i>funnelWidth</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [{ funnelWidth : '100' }];
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    series: [ { width: '100' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>Grouping</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>groupTo</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    series: [ { groupTo: '100' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>

<tr>
<td><b>GroupMode</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>groupMode</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    series: [ { groupMode: 'Point' }];
});
chart.appendTo('#chart);
</code>
</td>
</tr>
</table>

## DataLabel

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>dataLabel</b></td>
<td>
<b>Property</b>:<i>series.marker.dataLabel</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ visible: true }}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.dataLabel</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { visible: true }}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>border of dataLabel</b></td>
<td>
<b>Property</b>:<i>series.marker.dataLabel.border</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ border: { color: 'red', width: 2 }}}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { border: { color: 'red', width: 2}}}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>connector style for dataLabel connector line</b></td>
<td>
<b>Property</b>:<i>connectorLine</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ connectorLine: { type: 'Curve', width: 2 }}}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>connectorStyle</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { connectorStyle: { type: 'Curve', width: 2 }}}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>Fill for dataLabel</b></td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ fill: 'red' }}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { fill: 'pink'}}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>font for dataLabel</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ font: { } }}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { font: { }}}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>font for dataLabel</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ font: { } }}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { font: { }}}
});
pie.appendTo('#chart');
</code></td>
</tr>

<tr>
<td><b>position</b></td>
<td>
<b>Property</b>:<i>position</i>
</br>
</br>
<code>
$("#chart").ejChart({
    series: [
        { marker: { dataLabel :{ position: 'Inside' }}}
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
let pie: AccumulationChart = new AccumulationChart({
    series: { dataLabel : { position: 'Outside' }}
});
pie.appendTo('#chart');
</code></td>
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
let chart: AccumulationChart = new AccumulationChart({
    series: [ {dataLabel: { rx: 10 } }];
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
let chart: AccumulationChart = new AccumulationChart({
    series: [ {dataLabel: { ry: 10 } }];
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
let chart: AccumulationChart = new AccumulationChart({
    series: [ {dataLabel: { template: '<div>Chart</div>' }  }];
});
chart.appendTo('#chart);
</code>
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
   legend: { font: { fontFamily: '', fontWeight: '400', fontStyle: 'italic', size: '12' } }
});
</code>
</td>
<td>
<b>Property</b>:<i>textStyle</i>
</br>
</br>
<code>
let chart: AccumulationChart = new AccumulationChart({
    legendSettings: { textStyle: { size: '12' , color: 'red', fontFamily: 'Italic', fontWeight: '400', fontStyle: 'Normal', opacity: 1, textAlignment: 'Center', textOverFlow: 'Trim'} }
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({

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
let chart: AccumulationChart = new AccumulationChart({

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
let chart: AccumulationChart = new AccumulationChart({

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
let chart: AccumulationChart = new AccumulationChart({

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
let chart: AccumulationChart = new AccumulationChart({

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
let chart: AccumulationChart = new AccumulationChart({
    animationComplete: () => {
    }
});
chart.appendTo('#chart');
</code>
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
    textRender: () => {
    }
});
chart.appendTo('#chart');
</code>
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
    load: () => {
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
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
let chart: AccumulationChart = new AccumulationChart({
    pointRender : () => {
    }
});
chart.appendTo('#chart');
</code>
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
let chart: AccumulationChart = new AccumulationChart({
    seriesRender : () => {
    }
});
chart.appendTo('#chart');
</code>
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
let chart: AccumulationChart = new AccumulationChart({
    tooltipRender : () => {
    }
});
chart.appendTo('#chart');
</code>
</td>
</tr>

</table>