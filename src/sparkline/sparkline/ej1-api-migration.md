---
title: "Migration from Essential JS 1"
component: "Sparkline"
description: "Explains the common steps for migrating from Essential JS 1 application to Essential JS 2 components especially, sparkline component."
---

# Migration from Essential JS 1

This article describes the API migration process of Accordion component from Essential JS 1 to Essential JS 2.

## Sparkline Types

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Type| **Property:** *type*<br/><br/> $("#container").ejSparkline({ type : 'line' }); |**Property:** *type*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; type: 'Line' <br/> }); <br/> sparkline.appendTo('#container');|

## Databinding

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Datasource| **Property:** *dataSource*<br/><br/> $("#container").ejSparkline({ dataSource : 'data' }); |**Property:** *dataSource*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataSource: data <br/> }); <br/> sparkline.appendTo('#container');|
|Binding X values with datasource| **Property:** *xName*<br/><br/> $("#container").ejSparkline({ xName : "XValue" }); |**Property:** *xName*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; xName: 'XValue' <br/> }); <br/> sparkline.appendTo('#container');|
|Binding Y values with datasource| **Property:** *yName*<br/><br/> $("#container").ejSparkline({ yName : "YValue" }); |**Property:** *yName*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; yName: 'YValue' <br/> }); <br/> sparkline.appendTo('#container');|

## Markers

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable markers| **Property:** *markerSettings.visible*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ visible : true } <br/>}); |**Property:** *markerSettings.visible*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; visible: ['All'] <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Color| **Property:** *markerSettings.fill*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ fill : "green" } <br/>}); |**Property:** *markerSettings.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; fill: "green" <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Size| **Property:** *markerSettings.width*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ width : 5 } <br/>}); |**Property:** *markerSettings.size*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; size: 5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Opacity| **Property:** *markerSettings.opacity*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ opacity : 0.5 } <br/>}); |**Property:** *markerSettings.opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; opacity: 0.5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border color| **Property:** *markerSettings.border.color*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ <br/> &nbsp; &nbsp; border: { color: "green" } } <br/>}); |**Property:** *markerSettings.border.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; border: { fill: 'green' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border width| **Property:** *markerSettings.border.width*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ <br/> &nbsp; &nbsp; border: { width: 2 } } <br/>}); |**Property:** *markerSettings.border.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; markerSettings: { <br/> &nbsp; &nbsp; border: { width: 2 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border opacity| **Property:** *markerSettings.border.opacity*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; markerSettings :{ <br/> &nbsp; &nbsp; border: { opacity: 0.7 } } <br/>}); |Not applicable|

## Data labels

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable data labels| Not applicable |**Property:** *dataLabelSettings.visible*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; visible: ['All'] <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Color| Not applicable |**Property:** *dataLabelSettings.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; fill: "green" <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Size| Not applicable |**Property:** *dataLabelSettings.size*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; size: 5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Opacity| Not applicable |**Property:** *dataLabelSettings.opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; opacity: 0.5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border color| Not applicable |**Property:** *dataLabelSettings.border.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; border: { fill: 'green' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border width| Not applicable |**Property:** *dataLabelSettings.border.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; border: { width: 2 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Format| Not applicable |**Property:** *dataLabelSettings.format*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; format: '${xval}: ${yval}' <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Horizontal Offset| Not applicable |**Property:** *dataLabelSettings.offset.x*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; offset: { x: 10 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Vertical Offset| Not applicable |**Property:** *dataLabelSettings.offset.y*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; offset: { y: 10 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font color| Not applicable |**Property:** *dataLabelSettings.textStyle.color*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { color: 'black' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font family| Not applicable |**Property:** *dataLabelSettings.textStyle.fontFamily*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { fontFamily: 'Arial' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font style| Not applicable |**Property:** *dataLabelSettings.textStyle.fontStyle*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { fontStyle: 'normal' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font weight| Not applicable |**Property:** *dataLabelSettings.textStyle.fontWeight*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { fontWeight: 'bold' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font opacity| Not applicable |**Property:** *dataLabelSettings.textStyle.opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { opacity: 0.7 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font size| Not applicable |**Property:** *dataLabelSettings.textStyle.fontSize*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; dataLabelSettings: { <br/> &nbsp; &nbsp; textStyle: { fontSize: '12px' } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|

## Range band

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Color| **Property:** *rangeBandSettings.fill*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; rangeBandSettings :{ fill : "green" } <br/>}); |**Property:** *rangeBandSettings.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; rangeBandSettings: { <br/> &nbsp; &nbsp; fill: "green" <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Opacity| **Property:** *rangeBandSettings.opacity*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; rangeBandSettings :{ opacity : 0.5 } <br/>}); |**Property:** *rangeBandSettings.opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; rangeBandSettings: { <br/> &nbsp; &nbsp; opacity: 0.5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Start range| **Property:** *rangeBandSettings.startRange*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; rangeBandSettings :{ <br/> &nbsp; &nbsp; startRange: 5 <br/> &nbsp;} <br/>}); |**Property:** *rangeBandSettings.startRange*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; rangeBandSettings: { <br/> &nbsp; &nbsp; startRange: 5 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|End range| **Property:** *rangeBandSettings.endRange*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; rangeBandSettings :{ <br/> &nbsp; &nbsp; endRange: 10 <br/> &nbsp;} <br/>}); |**Property:** *rangeBandSettings.endRange*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; rangeBandSettings: { <br/> &nbsp; &nbsp; endRange: 10 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|

## Special points customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|High point color| **Property:** *highPointColor*<br/><br/> $("#container").ejSparkline({ highPointColor: 'green' }); |**Property:** *highPointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ highPointColor: 'green' }); <br/> sparkline.appendTo('#container');|
|Low point color| **Property:** *lowPointColor*<br/><br/> $("#container").ejSparkline({ lowPointColor: 'red' }); |**Property:** *lowPointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ lowPointColor: 'red' }); <br/> sparkline.appendTo('#container');|
|Negative point color| **Property:** *negativePointColor*<br/><br/> $("#container").ejSparkline({ negativePointColor: 'orange' }); |**Property:** *negativePointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ negativePointColor: 'orange' }); <br/> sparkline.appendTo('#container');|
|Start point color| **Property:** *startPointColor*<br/><br/> $("#container").ejSparkline({ startPointColor: 'orange' }); |**Property:** *startPointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ startPointColor: 'orange' }); <br/> sparkline.appendTo('#container');|
|End point color| **Property:** *endPointColor*<br/><br/> $("#container").ejSparkline({ endPointColor: 'orange' }); |**Property:** *endPointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ endPointColor: 'orange' }); <br/> sparkline.appendTo('#container');|
|Tie point color| **Property:** *tiePointColor*<br/><br/> $("#container").ejSparkline({ tiePointColor: 'orange' }); |**Property:** *tiePointColor*<br/><br/> let sparkline: Sparkline = new Sparkline({ tiePointColor: 'orange' }); <br/> sparkline.appendTo('#container');|

## Axis customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show axis line| **Property:** *axisSettings.visible*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; axisSettings :{ <br/> &nbsp; &nbsp; visible: true <br/> &nbsp;} <br/>}); |**Property:** *axisSettings.lineSettings.visible*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; lineSettings: { visible: true } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Line color| **Property:** *axisSettings.color*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; axisSettings :{ <br/> &nbsp; &nbsp; color: "green" <br/> &nbsp;} <br/>}); |**Property:** *axisSettings.lineSettings.color*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; lineSettings: { color: "green" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Line width| **Property:** *axisSettings.width*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; axisSettings :{ <br/> &nbsp; &nbsp; width: 2 <br/> &nbsp;} <br/>}); |**Property:** *axisSettings.lineSettings.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; lineSettings: { width: 2 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Dash array| **Property:** *axisSettings.dashArray*<br/><br/> $("#container").ejSparkline({ <br/>&nbsp; axisSettings :{ <br/> &nbsp; &nbsp; dashArray: [5, 2] <br/> &nbsp;} <br/>}); |**Property:** *axisSettings.lineSettings.dashArray*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; lineSettings: { dashArray: [5, 2] } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|X axis minimum value| Not applicable |**Property:** *axisSettings.minX*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; minX: 0 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|X axis maximum value| Not applicable |**Property:** *axisSettings.maxX*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; maxX: 100 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Y axis minimum value| Not applicable |**Property:** *axisSettings.minY*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; minY: 0 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Y axis maximum value| Not applicable |**Property:** *axisSettings.maxY*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; maxY: 0 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Horizontal axis line position| Not applicable |**Property:** *axisSettings.value*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; axisSettings: { <br/> &nbsp; &nbsp; value: 10 <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|

## Appearance customization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Background color| **Property:** *background*<br/><br/> $("#container").ejSparkline({ background: "gray" }); |**Property:** *containerArea.background*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; containerArea: { background: "gray" } <br/> }); <br/> sparkline.appendTo('#container');|
|Border color | Not applicable |**Property:** *containerArea.border.color*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; containerArea: { <br/> &nbsp; &nbsp; border: { color: "green" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Border width | Not applicable |**Property:** *containerArea.border.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; containerArea: { <br/> &nbsp; &nbsp; border: { width: 2 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Series color| **Property:** *fill*<br/><br/> $("#container").ejSparkline({ fill: "green" }); |**Property:** *fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ fill : "green" }); <br/> sparkline.appendTo('#container');|
|Series opacity| **Property:** *opacity*<br/><br/> $("#container").ejSparkline({ opacity: 0.5 }); |**Property:** *opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ opacity : 0.5 }); <br/> sparkline.appendTo('#container');|
|Line series width| **Property:** *width*<br/><br/> $("#container").ejSparkline({ width: 3 }); |**Property:** *lineWidth*<br/><br/> let sparkline: Sparkline = new Sparkline({ lineWidth : 3 }); <br/> sparkline.appendTo('#container');|
|Series border color| **Property:** *border.color*<br/><br/> $("#container").ejSparkline({ border: { color: "green" } }); |**Property:** *border.color*<br/><br/>let sparkline: Sparkline = new Sparkline({ border: { color: "green" } });<br/>sparkline.appendTo('#container');|
|Series border width| **Property:** *border.width*<br/><br/> $("#container").ejSparkline({ border: { width: 2 } }); |**Property:** *border.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ border: { width: 2 } }); <br/> sparkline.appendTo('#container');|
|Series palette| **Property:** *palette*<br/><br/> $("#container").ejSparkline({ palette: "colorFieldNameInDatasource" }); |**Property:** *palette*<br/><br/> let sparkline: Sparkline = new Sparkline({ palette : ["green", "red", "yellow"] }); <br/> sparkline.appendTo('#container');|
|Theme| **Property:** *theme*<br/><br/> $("#container").ejSparkline({ theme: "Azure" }); |**Property:** *theme*<br/><br/> let sparkline: Sparkline = new Sparkline({ theme : "Material" }); <br/> sparkline.appendTo('#container');|
|Width| **Property:** *size.width*<br/><br/> $("#container").ejSparkline({ size: { width: "100%" } }); |**Property:** *width*<br/><br/> let sparkline: Sparkline = new Sparkline({ width : "100%" }); <br/> sparkline.appendTo('#container');|
|Height| **Property:** *size.height*<br/><br/> $("#container").ejSparkline({ size: { height: "200px" } }); |**Property:** *height*<br/><br/> let sparkline: Sparkline = new Sparkline({ height : "200px" }); <br/> sparkline.appendTo('#container');|

## Tooltip

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Show tooltip| **Property:** *tooltip.visible*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { visible: true } <br/> }); |**Property:** *tooltipSettings.visible*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { visible: true } <br/> }); <br/> sparkline.appendTo('#container');|
|Background| **Property:** *tooltip.fill*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { fill: "white" } <br/> }); |**Property:** *tooltipSettings.fill*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { fill: "white" } <br/> }); <br/> sparkline.appendTo('#container');|
|Format| Not applicable |**Property:** *tooltipSettings.format*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { format: "${xval}: ${yval}" } <br/> }); <br/> sparkline.appendTo('#container');|
|Template| **Property:** *tooltip.template*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { template: "tooltip" } <br/> }); |**Property:** *tooltipSettings.template*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { template: "tooltip" } <br/> }); <br/> sparkline.appendTo('#container');|
|Font color| **Property:** *tooltip.font.color*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { color: "gray" } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.color*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { color: "gray" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font opacity| **Property:** *tooltip.font.opacity*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { opacity: 0.8 } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.opacity*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { opacity: 0.8 } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font size| **Property:** *tooltip.font.size*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { size: "14px" } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.size*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { size: "14px" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font family| **Property:** *tooltip.font.fontFamily*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { fontFamily: "Arial" } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.fontFamily*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { fontFamily: "Arial" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font style| **Property:** *tooltip.font.fontStyle*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { fontStyle: "normal" } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.fontStyle*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { fontStyle: "normal" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Font weight| **Property:** *tooltip.font.fontWeight*<br/><br/> $("#container").ejSparkline({ <br/> &nbsp; tooltip: { <br/> &nbsp;&nbsp; font: { fontWeight: "bold" } <br/> &nbsp; } <br/> }); |**Property:** *tooltipSettings.textStyle.fontWeight*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; textStyle: { fontWeight: "bold" } <br/> &nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Enable track line| Not applicable |**Property:** *tooltipSettings.trackLineSettings.visible*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; trackLineSettings: { visible: true } <br/>&nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Track line color| Not applicable |**Property:** *tooltipSettings.trackLineSettings.color*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; trackLineSettings: { color: "red" } <br/>&nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|
|Track line width| Not applicable |**Property:** *tooltipSettings.trackLineSettings.width*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/> &nbsp; tooltipSettings: { <br/> &nbsp;&nbsp; trackLineSettings: { width: 2 } <br/>&nbsp; } <br/> }); <br/> sparkline.appendTo('#container');|

## Rendering

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Enable canvas rendering| **Property:** *enableCanvasRendering*<br/><br/> $("#container").ejSparkline({ enableCanvasRendering : true }); | Not applicable |

## Localization

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Localization| **Property:** *locale*<br/><br/> $("#container").ejSparkline({ locale : "en-US" }); | **Property:** *type*<br/><br/> let sparkline: Sparkline = new Sparkline({ locale: 'en-US' }); <br/> sparkline.appendTo('#container'); |

## Methods

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Dynamically updating sparkline| **Method:** *redraw*<br/><br/> $("#container").ejSparkline("redraw"}}); | **Method:** *refresh*<br/><br/> sparkline.refresh(); |
|Append sparkline to element| Not applicable | **Method:** *appendTo*<br/><br/> sparkline.appendTo("#container"); |

## Events

| **Behavior** | **API in Essential JS 1** | **API in Essential JS 2** |
| --- | --- | --- |
|Load| **Event:** *load*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;load: function(args) { } <br/> }); | **Event:** *load*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; load: function(e: ISparklineLoadEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Load completed| **Event:** *loaded*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;loaded: function(args) { } <br/> }); | **Event:** *loaded*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; loaded: function(e: ISparklineLoadedEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Initialize tooltip| **Event:** *tooltipInitialize*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;tooltipInitialize: function(args) { } <br/> }); | **Event:** *tooltipInitialize*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; tooltipInitialize: function(e: ITooltipRenderingEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Series rendering| **Event:** *seriesRendering*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;seriesRendering: function(args) { } <br/> }); | **Event:** *seriesRendering*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; seriesRendering: function(e: ISeriesRenderingEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Region mouse move| **Event:** *pointRegionMouseMove*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;pointRegionMouseMove: function(args) { } <br/> }); | **Event:** *pointRegionMouseMove*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; pointRegionMouseMove: function(e: IPointRegionEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Region click| **Event:** *pointRegionMouseClick*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;pointRegionMouseClick: function(args) { } <br/> }); | **Event:** *pointRegionMouseClick*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; pointRegionMouseClick: function(e: IPointRegionEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Mouse move| **Event:** *sparklineMouseMove*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;sparklineMouseMove: function(args) { } <br/> }); | **Event:** *sparklineMouseMove*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; sparklineMouseMove: function(e: ISparklineMouseEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|Mouse leave| **Event:** *sparklineMouseLeave*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;sparklineMouseLeave: function(args) { } <br/> }); | Not applicable |
|Click| **Event:** *click*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;click: function(args) { } <br/> }); | **Event:** *sparklineMouseClick*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; sparklineMouseClick: function(e: ISparklineMouseEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|doubleClick| **Event:** *doubleClick*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;doubleClick: function(args) { } <br/> }); | Not applicable |
|rightClick| **Event:** *rightClick*<br/><br/> $("#container").ejSparkline({<br/>&nbsp;rightClick: function(args) { } <br/> }); | Not applicable |
|axisRendering| Not applicable | **Event:** *axisRendering*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; axisRendering: function(e: IAxisRenderingEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|dataLabelRendering| Not applicable | **Event:** *dataLabelRendering*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; dataLabelRendering: function(e: IDataLabelRenderingEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|markerRendering| Not applicable | **Event:** *markerRendering*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; markerRendering: function(e: IMarkerRenderingEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|pointRendering| Not applicable | **Event:** *pointRendering*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; pointRendering: function(e: ISparklinePointEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |
|resize| Not applicable | **Event:** *resize*<br/><br/> let sparkline: Sparkline = new Sparkline({ <br/>&nbsp; resize: function(e: ISparklineResizeEventArgs): void { }  <br/>}); <br/> sparkline.appendTo('#container'); |